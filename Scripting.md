---
layout: default
title: Scripting
nav_order: 5
---

# Weasel scripting - reference guide

This page lists methods and attribute for scripting pipelines in weasel. 

# Weasel methods

Weasel methods are methods of the `weasel` object, which is available in any script as the argument of main(weasel). 

Weasel methods can be used to retrieve DICOM data selected by the user (get-type functionality), or to update the weasel interface or launch dedicated displays from within a pipeline (set-type functionality).

## Weasel retrieve methods (get-type)

```markdown

# Get the images checked by the user in the display. 

images = weasel.images()

# Get the series checked by the user in the display. 

series = weasel.series()

# Get the studies checked by the user in the display. 

studies = weasel.studies()

# Get the subjects checked by the user in the display. 

subjects = weasel.subjects()

```

## Weasel update methods (set-type)

```markdown

# 

```


# Dicom project methods





