---
layout: default
title: Scripting
nav_order: 5
---

# Weasel scripting: reference guide

This page lists methods for scripting pipelines in `weasel`. For examples please see the pipeline tutorials page.

*Weasel methods* are methods of the `weasel` object, which is available in any script as the argument of main(weasel). 

Weasel methods can be used to retrieve DICOM data selected by the user, or to update the weasel interface or launch dedicated displays from within a pipeline.

*DICOM object methods* are methods to retrieve and modify DICOM data. 

```markdown
# Retrieve DICOM objects
weasel.images()
weasel.series()
weasel.studies()
weasel.subjects()
# DICOM object methods
dicom_object.copy()
dicom_object.delete()
dicom_object.merge()
dicom_object.children()
dicom_object.parent()
# Write DICOM 
dicom_object[KeyWord] = value
# Messaging to the user
weasel.message()
weasel.close_message()
weasel.information()
weasel.question()
weasel.progress_bar()
weasel.update_progress_bar()
weasel.close_progress_bar()
# Launching and updating displays
weasel.refresh()
weasel.close_all_windows()
weasel.user_input()
```

# Retrieve DICOM objects

A collection of methods to retrieve data in the DICOM hierarchy that are checked by the user in the tree view. 

```markdown
weasel.images()
weasel.series()
weasel.studies()
weasel.subjects()
```

```markdown
images = weasel.images()
# Get the images checked by the user. 
series = weasel.series()
# Get the series checked by the user.
studies = weasel.studies() 
# Get the studies checked by the user.
subjects = weasel.subjects() 
# Get the subjects checked by the user. 
```

# Write DICOM

```markdown
dicom_object[`label`] = `value`
# Overwrite DICOM data element specified by `label` with `value`. Here `label` is either a DICOM keyword or a `(group, element)` pair of hexadecimal tags. Examples:
    dicom_object["SliceLocation"] = 10.3
    dicom_object["SeriesDescription"] = "New Series"
``` 

# DICOM object methods
A collection of methods to retrieve and update DICOM data elements. 

In the definitions below, `dicom_object` can be a list of `images`, `series`, `studies` or `subjects`, or else a single item in one of those lists.

```markdown
dicom_object.copy()
dicom_object.delete()
dicom_object.merge()
dicom_object.children()
dicom_object.parent()
```

```markdown
new_dicom_object = dicom_object.copy()
# Create a copy of the DICOM object
# Defined for: 
# 	images (single or list)
#	series (single or list)
#	studies (single or list)
#	subjects (single or list)
dicom_object.delete()	 
# Delete the DICOM object 
# Defined for: 
# 	images (single or list)
#	series (single or list)
#	studies (single or list)
#	subjects (single or list)
new_dicom_object = dicom_object.merge()
# Merge a list of DICOM objects into a new object
# Defined for: 
# 	images (list)
#	series (list)
#	studies (list)
#	subjects (list)
new_dicom_object = dicom_object.children()
# Get a list of children
# Defined for: 
#	series (single or list)
#	studies (single or list)
#	subjects (single or list)
new_dicom_object = dicom_object.parent()
# Get the parent object
# Defined for: 
# 	images (single or list)
#	series (single or list)
#	studies (single or list)
#	subjects (single or list)
```

# Messaging to the user

```markdown
weasel.message()
weasel.close_message()
weasel.information()
weasel.question()
weasel.progress_bar()
weasel.update_progress_bar()
weasel.close_progress_bar()
```

```markdown
weasel.message(msg="Hi there! Please be patient while I work this out", title="Totally pointless message")
# Launch a message window.
weasel.close_message()
# Close the message pop-up window
weasel.information(msg="Please click OK so we can move on!", title="Totally pointless information")
# Launch an information window. 
# The user must press 'OK' to continue.
answer = weasel.question(msg="Shall we carry on?", title="My burning question")
# Launch a question window. 
# The user has to click either "OK" or "Cancel" in order to continue. 
# The answer is True if the user clicks "OK" and False if they click "Cancel".
weasel.progress_bar(max=1, index=0, msg="Here's where we are so far", title="Progress Bar")
# Launch a progress bar - typically used to update on the status of long calculations. 
# max is used to show the progress as a percentage.
# index is the current state shown in the progress bar.
weasel.update_progress_bar(index=0) 
# Update an existing progress bar with a new index. 
# While a new progress bar can be launched at each iteration, this slows down calculations a lot. 
# It is significantly faster to launch the progress bar outside the loop, 
# and then use this method to update its value inside the loop.
weasel.close_progress_bar()
# Close an existing progress bar
```

# Launching and updating displays

A collection of methods to launch or manipulate dedicated displays.

```markdown
weasel.refresh()
weasel.close_all_windows()
weasel.user_input()
```

```markdown
weasel.refresh()
# Refresh weasel. 
# This will update the state of all displays that are currently open.
# A refresh is typically done at the of a processing pipeline, or at intermediate stages of very long pipelines.
weasel.close_all_windows()
# Close all open windows, except for the tree view.
weasel.user_input()
# Widget for getting input from the user.

```








