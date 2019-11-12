---
layout: post
title: Code Signing Error ofxSyphon
---

If your using the latest XCode (11.0 (11A420a)) then there are a number of code signing issues around using Openframeworks - for example, needing to use the latest build, rather than stable release.

If you want to use the ofxSyphon plugin, you'll hit some problems as well, so here's how to fix them.

## The Error

You should get the error `Command CodeSign failed with a nonzero exitcode` this is caused by ofxSyphon not being code signed - as required by XCode now.

![error][error]

## The Fix

It's an easy fix, we just need to update out build settings to set the `Other Code Signing Flags` to `--deep` - the only challenge is these are a little buried.

### Step 1

Click, on the root level project in the left sidebar - this opens the project settings in the main pane.

![step1][step1]

### Step 2

Click on the `Build Settings` header / tab in the mane pane. This will give us all the things which ocntrol build - `Other Code Signing Flags` is in here somewhere - luckily we can use search in the top right of the main pane to find it.

![step2][step2]

Enter `Code Sign` in here, and the build settings should filter down to just the relevant ones

![step3][step3]

## Step 3

Double clicking the `Other Code Signing Flags` line where the value should be, opens up a dialog which allows values to be added / deleted.

![step4][step4]

Clicking the plus sign here, will allow you to enter text in the top line of the dialog, and you can add `--deep` 

## Step 4

Save and rebuild - the error should now be gone.

[error]: /localImages/of/ofxSyphon/001_error.png
[step1]: /localImages/of/ofxSyphon/002_projectSettings.png
[step2]: /localImages/of/ofxSyphon/002_BuildSettings.png
[step3]: /localImages/of/ofxSyphon/003_search.png
[step4]: /localImages/of/ofxSyphon/004_setDeep.png
