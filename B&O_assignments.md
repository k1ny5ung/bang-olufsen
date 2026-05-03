# Software QA Technical Assignment

INSTRUCTIONS
============

- This task will be reviewed by the Bang & Olufsen QA team. To maintain anonymity, please do not provide your name, email address, or any other personal identifiable information in the submission files.

- Please download assignment from this repository. Do NOT create pull requests to this repository.

- Please share your solution with us via GitHub repository and provide the repository link in your email. Ensure your repository is public or accessible with the appropriate permissions.

- Please provide relevant documentation of your work in markdown file format, and feel free to mention references for your work if you have used any.

- If you used any AI tool or LLM model while completing this assignment, please also answer the following in a separate document file:
	- Which AI tool or LLM model did you use, and why did you choose it?
	- How did you use it during the assignment?
	- Approximately how much time did you spend using it?
	- Which part of your solution benefited the most from it?
	- What was the biggest drawback or limitation?
	- How did you validate the AI-generated output before submitting your final answer?
	- Were there any suggestions from the AI tool that you decided not to use? Why?
	- What part of the final submission best reflects your own independent reasoning?


ASSIGNMENT
==========

### Assignment 1:

You are joining a software quality team working on wireless headphones/earbuds and their companion mobile application on iOS and Android. The team is preparing to release a new feature for a premium audio product.

Feature under test: **Adaptive Listening Modes**

The mobile app allows the user to connect their headphones/earbuds and control listening modes.
The new feature includes:

	- switching between: Noise Cancellation and Transparency Mode
	- saving the user’s last selected mode
	- automatically restoring the last selected mode when the device reconnects
	- showing battery level for: left earbud, right earbud, charging case
	- showing connection status in the app
	- allowing listening mode change only when the product is connected
	- preventing listening mode switching when the battery is critically low
	- supporting both iOS and Android

Expected behavior:

	- The user can change listening mode only when the device is connected
	- The selected listening mode should be applied to the device within 2 seconds
	- The selected listening mode shown in the app must match the actual mode active on the device
	- The last selected mode should persist after app restart
	- The last selected mode should be restored after reconnect
	- Battery levels shown in the app should reflect the device state correctly
	- If the battery is below 5%, mode switching is blocked, and the app should display a clear message
	- The feature should behave consistently on both iOS and Android

Additional real-world context:

	- Some users update the app but not the device firmware
	- Bluetooth connection quality may vary in real environments
	- Users may switch between phone call audio and music playback
	- Users expect a quick, reliable response because this is a premium product

Based on the above-provided information, perform the following tasks:

#### Task 1: 

Review the feature description and identify unclear or missing requirements, assumptions you would need to test effectively, top quality risks you would raise before test execution starts

##### [Unclear or Missing Requirements]

 - Does the restriction on operation when the battery is below 5% apply to both earbuds simultaneously, or does it trigger if even just one earbud falls below 5%?
 - What are the specific criteria for defining when "Listening Mode" has been successfully applied? (e.g., Is it based on the display change within the app?)
 - Is the data for the changed mode stored only within the app, or is it also saved to the earbud's internal memory?
 - What is the maximum allowable version gap for guaranteed compatibility between the software and the device firmware?
 - Is the signal strength sufficient to prevent data loss across the specified distance between the smartphone and the device?
 
##### [Assumptions Required for Effective Testing]

- Firmware/App Compatibility: It is assumed that performance is identical across both iOS and Android platforms.
- Minimum Supported Version: It is assumed there is a minimum supported firmware version, and all features function correctly on that version or higher.
- Version Detection: It is assumed the app detects outdated firmware and displays an appropriate notification (e.g., "Update Required").
- Battery Data Integrity: The device’s reported battery level is assumed to be reliable and accurate data for testing purposes.
- Low Battery Threshold: Clarification is needed on whether the "below 5% battery" restriction applies when only one earbud reaches that level or only when both do.
- App Reinstallation: Upon reinstalling the app, will settings revert to default values, or will they be restored from cached data?
- It is assumed that only one device acts as the "Primary Connection" for the earbuds at any given time (Note: Multipoint support needs to be specified).
- Battery Data Reliability: It is assumed that the battery values reported by the device are reliable (Note: These values will be controlled via firmware simulators or testing tools during the test).

##### [Core Quality Risks to Address Before Test Execution]

- App-Device State Mismatch (Highest Priority): Discrepancies between the settings shown in the app and the actual state of the device.
- Mode Switching Latency: Delays exceeding 2 seconds when changing modes.
- Incorrect Mode Restoration: Failure to restore the correct mode upon reconnection.
- Inaccurate Battery Reporting: Displaying incorrect battery information or synchronization errors.
- iOS/Android Behavioral Disparity: Inconsistent performance or logic between the two operating systems.
- Firmware Version Incompatibility: Errors or bugs caused by version gaps between the app and firmware.
- Bluetooth Environmental Interference: Performance degradation due to signal interference or distance.
- Transition Errors: System failures occurring during the switch between phone calls and music playback.

##### [Test Considerations & Edge Cases]

- Stress Testing: Perform high-speed, repetitive operations to verify system stability.
- Exception Handling: Define behavior for scenarios where the app is force-closed or the smartphone unexpectedly powers off.
- Legacy Firmware Constraints: Clearly define the functional limitations of older firmware versions.
- In-Call Mode Switching: Verify if mode changes are permitted during an active call and, if so, ensure they are applied correctly.
- Battery Sync Interval: Confirm whether battery information is synchronized at regular periodic intervals.

#### Task 2: 

Describe your test approach for this feature:

	- what you would test first and why
	- what areas would you prioritize most
	- what you would focus on in exploratory testing
	- what regression areas would you consider important
	- how you would think about coverage across iOS and Android

#### Task 3: 

Write between 05-10 high-value test scenarios for this feature.

#### Task 4: 

Write at least 2 detailed test cases in a standard format

#### Task 5: 

During testing, you observe the following issue:

	- The user selects Transparency Mode in the app while the earbuds are connected. The app immediately updates and shows Transparency Mode as active. However, the earbuds remain in Noise Cancellation for around 8–12 seconds. In some cases, after placing the earbuds back in the case and reconnecting, the app still shows Transparency Mode, but the earbuds are actually in Noise Cancellation Mode.

Write a bug report as you would submit it to the development team.

#### Task 6: 

Describe how you would explore this feature beyond scripted testing. Please include the kinds of real-world situations you would investigate for headphones/earbuds.

#### Task 7: 

Assume these issues were found near release:

	- On Android, listening mode changes sometimes take 4 seconds instead of 2 seconds
	- On iOS, the battery-low warning is present, but the wording is confusing
	- In 1 out of 25 reconnect attempts, the app restores the previous mode visually, but the earbuds actually reconnect in a different mode

Would you recommend: release, conditional release, or no release? Explain your reasoning.

### Assignment 2:  

In the provided Wireshark trace of a Bluetooth audio streaming session between a headset and a smartphone. The user reports audio cuts after a few seconds. Provide step-by-step approach on how you would analyze the issue? Please refer to the contents of the file: *A2DP_audio_drops.7z*

### Assignment 3: 

The attached zip file *TWS_User_Scenario_EXT.7z* contains Wireshark logs for a TWS Bluetooth audio system. 
	- Analyse the logs and find out the roles of each device
	- Find out the primary user scenario covered in the logs
	- Explain the analysis steps. 
