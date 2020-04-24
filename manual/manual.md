Alva Port Progress
- [ ] Scripts
	- [x] DrivingErrorHandler
	- [x] ErrorMessageController v2
		- [x] Buttons
	- [ ] SpeedLimitError
	- [ ] StopDetector
	- [ ] Checkpoint
	- [ ] CheckpointSingleton
	- [ ] OnewayError
		- [ ] Enable
		- [ ] Disable
	- [ ] StopLightTracker
		- [ ] East
		- [ ] West
		- [ ] North
		- [ ] South 
	- [ ] InappropriateStop
	- [ ] OffCourseError
	- [ ] ParkingArea
	- [ ] PlayerCollisionDetector
	- [ ] WrongLane
- [ ] Prefabs
	- [x] ErrorCanvas v2
	- [x] Speed Tester
	- [x] Stop Tester
	- [x] Oneway Triggers
	- [ ] Traffic Lights 
	- [ ] ReportCard
	- [ ] MetaErrorController
	- [ ] Checkpoint
	- [ ] ParkingArea
- [ ] External Dependencies
	- [x] TextMeshPro
	- [x] SlimUI

# MTSU CSCI 4700/5700
## Spring 2020 — Driving Error Detection
## Team
- Abhilash Patel — UI Team
- Devon Wilson — Engineering Team, Architecture & Porting
- Dessa Hale — UI Team, Team Communication & Management
- Ian Gregory — Engineering Team
- Josh Ortner — Engineering Team
- Michell Knabe — Engineering Team
- Nibraas Khan — Engineering Team, Project Manager
- L. K. ‘Silk’ Silkeutsabay — Engineering Team
- Tanzeena Karim — UI Team
- Zane Sims — UI Team, Lead

---

## External Dependencies
- Unity Asset Store
	-  SlimUI - Tech Menu
		- For translucent menus
		- Depended on by:
			- Files in /Assets/Material/ErrorHandling/
- Unity Packages
	- TextMesh Pro v1.3.0
	- Depended on by:
		- /Assets/Prefabs/ErrorDetection/ErrorCanvas
		- Files in /Assets/Scripts/Error_Scripts/ErrorHandling/ErrorHandlingUI
---
## Files Added
- All files in the following directories and their subdirectories.
	- /Assets/Prefabs/ErrorDetection
	- /Assets/Materials/ErrorHandling
	- /Assets/Scripts/Error_Scripts/ErrorHandling

---

## Prefabs
### ErrorCanvas
Child of "Fove Interface" on "Car Variant3"
This is a TMPro GUI  rendered in world space within the car.  In order for the canvas to be fixed relative to the player's view it should be a child of whatever camera is selected as its event camera.  It is currently a child of the Fove Interface and is using the camera component of that object as its event camera.
The ErrorMessageController script lives on the top level object.
***For this to function correctly it must be a child of whatever object the camera the player looks through is attached to.  The script would have to be changed otherwise.***
### MetaErrorController
This is a container for the singletons Driving Error Handler and Checkpoint Singleton.
### SpeedTester
This prefab contains a trigger volume that changes the speed limit value on the player object's SpeedLimitError component.  It should be added as a child to a speed limit sign and have its Speed Limit field set appropriately.
### StopTester
---
## Scripts
### Namespace DrivingErrors
- #### DrivingErrorHandler
	- Placement — On the MetaErrorController Prefab
	- Purpose — Receiving messages from the error detection scripts and sending messages to the ErrorMessageController.
 
### Namespace DrivingErrors.UI
- #### ErrorMessageController
	- Placement — On the ErrorCanvas prefab
	- Purpose — Controls the error message UI elements
### Namepace DrivingErrors.UI.Buttons
- #### ContinueButton
	- Reload the scene from the previous checkpoint
- #### ExitButton
	- Currently call Application.Quit()
		- Should will be changed when the report card is added
- #### RestartButton
	- Resets the last checkpoint to the starting checkpoint then reloads the scene.
### Namespace DrivingErrors.ErrorDetection
- #### SpeedLimitError
	- Placed as a component on the speed tester prefab and the player car.
	- 