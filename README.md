# Expo Constants.appOwnership Undefined in Background Tasks

This repository demonstrates a bug where `Constants.appOwnership` returns `undefined` when accessed within a background task in an Expo managed workflow application.  This unexpected behavior can cause conditional logic errors within your app.

## Problem
The `Constants.appOwnership` API call, typically used to determine if the app is a development or production build, consistently returns `undefined` when executed within a background task (e.g., using `BackgroundTimer` or other background task APIs). This makes it impossible to reliably determine the app's ownership status in the background, hindering features that depend on this information.

## Solution
The solution involves handling the potential `undefined` return value of `Constants.appOwnership` and providing fallback behavior or alternative mechanisms to determine the app's ownership when needed within a background task.  This might include storing the ownership status in AsyncStorage upon app initialization.  Alternatively, you could use the `Constants.manifest` value to determine certain information such as whether the app is a development or production build. Note that the latter method will not be as reliable. 

## Steps to Reproduce
1. Clone this repository.
2. Follow the setup instructions in the `README` of each example (bug.js and bugSolution.js).
3. Run the app and trigger the background task. Observe the console logs, demonstrating the `undefined` issue and the workaround implemented in the solution. 
