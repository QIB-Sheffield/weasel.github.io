---
layout: default
title: Scripting
nav_order: 5
---

# Weasel scripting: reference guide

This page lists methods for scripting pipelines in `weasel`. For examples please see the pipeline tutorials page.

# Weasel methods

Weasel methods are methods of the `weasel` object, which is available in any script as the argument of main(weasel). 

Weasel methods can be used to retrieve DICOM data selected by the user, or to update the weasel interface or launch dedicated displays from within a pipeline.

## Retrieve DICOM objects

A collection of methods to retrieve data in the DICOM hierarchy that are checked by the user in the tree view. 

```markdown

# Get the images checked by the user. 
images = weasel.images()
# Get the series checked by the user. 
series = weasel.series()
# Get the studies checked by the user. 
studies = weasel.studies()
# Get the subjects checked by the user. 
subjects = weasel.subjects()

```
# DICOM data methods
A collection of methods to retrieve and update DICOM data elements. 

In the definitions below, *dicom_object* can be a list of images, series, studies or subjects, or else a single item in one fo those lists.

```markdown
# Create a copy of the DICOM object
new_dicom_object = dicom_object.copy()	  



```

## Messaging to the user

```markdown

# Launch a message window.
weasel.message(msg="Hi there! Please be patient while I work this out", title="Totally pointless message")

# Close the message pop-up window
weasel.close_message()

# Launch an information window. 
# The user must press 'OK' to continue.
weasel.information(msg="Please click OK so we can move on!", title="Totally pointless information")

# Launch a question window. 
# The user has to click either "OK" or "Cancel" in order to continue. 
# The answer is True if the user clicks "OK" and False if they click "Cancel".
answer = weasel.question(msg="Shall we carry on?", title="My burning question")

# Launch a progress bar - typically used to update on the status of long calculations. 
# max is used to show the progress as a percentage.
# index is the current state shown in the progress bar. 
weasel.progress_bar(max=1, index=0, msg="Here's where we are so far", title="Progress Bar")

# Update an existing progress bar with a new index. 
# While a new progress bar can be launched at each iteration, this slows down calculations a lot. 
# It is significantly faster to launch the progress bar outside the loop, 
# and then use this method to update its value inside the loop.
weasel.update_progress_bar(index=0)

# Close an existing progress bar
weasel.close_progress_bar()
```

## Launching and updating displays

A collection of methods to launch or manipulating dedicated displays.

```markdown

# Refresh weasel. 
# This will update the state of all displays that are currently open.
# A refresh is typically done at the of a processing pipeline, or at intermediate stages of very long pipelines.
weasel.refresh()

# Close all open windows, except for the tree view.
weasel.close_all_windows()

```








