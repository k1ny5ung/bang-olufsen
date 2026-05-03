Software QA Technical Assignment
INSTRUCTIONS
This task will be reviewed by the Bang & Olufsen QA team. To maintain anonymity, please do not provide your name, email address, or any other personal identifiable information in the submission files.

Please download assignment from this repository. Do NOT create pull requests to this repository.

Please share your solution with us via GitHub repository and provide the repository link in your email. Ensure your repository is public or accessible with the appropriate permissions.

Please provide relevant documentation of your work in markdown file format, and feel free to mention references for your work if you have used any.

If you used any AI tool or LLM model while completing this assignment, please also answer the following in a separate document file:

Which AI tool or LLM model did you use, and why did you choose it?
How did you use it during the assignment?
Approximately how much time did you spend using it?
Which part of your solution benefited the most from it?
What was the biggest drawback or limitation?
How did you validate the AI-generated output before submitting your final answer?
Were there any suggestions from the AI tool that you decided not to use? Why?
What part of the final submission best reflects your own independent reasoning?


ASSIGNMENT

<<< Assignment 1: >>>
You are joining a software quality team working on wireless headphones/earbuds and their companion mobile application on iOS and Android. The team is preparing to release a new feature for a premium audio product.

Feature under test: Adaptive Listening Modes

The mobile app allows the user to connect their headphones/earbuds and control listening modes. The new feature includes:

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

Task 1:
Review the feature description and identify unclear or missing requirements, assumptions you would need to test effectively, top quality risks you would raise before test execution starts

<Unclear or Missing Requirements>
- Does the restriction on operation when the battery is below 5% apply to both earbuds simultaneously, or does it trigger if even just one earbud falls below 5%?
- What are the specific criteria for defining when "Listening Mode" has been successfully applied? (e.g., Is it based on the display change within the app?)
- Is the data for the changed mode stored only within the app, or is it also saved to the earbud's internal memory?
- What is the maximum allowable version gap for guaranteed compatibility between the software and the device firmware?
- Is the signal strength sufficient to prevent data loss across the specified distance between the smartphone and the device?
 
<Assumptions Required for Effective Testing>
- Firmware/App Compatibility: It is assumed that performance is identical across both iOS and Android platforms.
- Minimum Supported Version: It is assumed there is a minimum supported firmware version, and all features function correctly on that version or higher.
- Version Detection: It is assumed the app detects outdated firmware and displays an appropriate notification (e.g., "Update Required").
- Battery Data Integrity: The device’s reported battery level is assumed to be reliable and accurate data for testing purposes.
- Low Battery Threshold: Clarification is needed on whether the "below 5% battery" restriction applies when only one earbud reaches that level or only when both do.
- App Reinstallation: Upon reinstalling the app, will settings revert to default values, or will they be restored from cached data?
- It is assumed that only one device acts as the "Primary Connection" for the earbuds at any given time (Note: Multipoint support needs to be specified).
- Battery Data Reliability: It is assumed that the battery values reported by the device are reliable (Note: These values will be controlled via firmware simulators or testing tools during the test).

<Core Quality Risks to Address Before Test Execution>
- App-Device State Mismatch (Highest Priority): Discrepancies between the settings shown in the app and the actual state of the device.
- Mode Switching Latency: Delays exceeding 2 seconds when changing modes.
- Incorrect Mode Restoration: Failure to restore the correct mode upon reconnection.
- Inaccurate Battery Reporting: Displaying incorrect battery information or synchronization errors.
- iOS/Android Behavioral Disparity: Inconsistent performance or logic between the two operating systems.
- Firmware Version Incompatibility: Errors or bugs caused by version gaps between the app and firmware.
- Bluetooth Environmental Interference: Performance degradation due to signal interference or distance.
- Transition Errors: System failures occurring during the switch between phone calls and music playback.

<Test Considerations & Edge Cases>
- Stress Testing: Perform high-speed, repetitive operations to verify system stability.
- Exception Handling: Define behavior for scenarios where the app is force-closed or the smartphone unexpectedly powers off.
- Legacy Firmware Constraints: Clearly define the functional limitations of older firmware versions.
- In-Call Mode Switching: Verify if mode changes are permitted during an active call and, if so, ensure they are applied correctly.
- Battery Sync Interval: Confirm whether battery information is synchronized at regular periodic intervals.



Task 2:
Describe your test approach for this feature:

- what you would test first and why
 -> Basic Connectivity after Power Cycles: Verification of standard connection recovery after a normal Power Off/On—this is a fundamental prerequisite for all operations.
 -> UI and Hardware Responsiveness: Verification that basic buttons and app menus function correctly and are applied immediately within 2 seconds.
 -> Smoke test: Verify that the core functions are executing without issues.

- what areas would you prioritize most
 : Sanity test after smoke: all new features work correctly without any issue
- what you would focus on in exploratory testing 
 : Verify that when a call is received during music playback, the audio correctly pauses and then resumes/stops as expected after the call ends.
 : Ensure that basic system functions or high-priority apps operate normally and that notifications/messages are displayed correctly.

- what regression areas would you consider important
 : Verify that the addition of new features has not negatively impacted existing basic connectivity and controls, such as play, pause, volume, and calls.
 : Ensure the device is operating correctly according to the currently displayed mode.
 : Check if mode-switching operations are restricted based on the battery level.
 : Confirm that control and manipulation are only possible while the device is connected.

- how you would think about coverage across iOS and Android
 : The basic stability of Android may vary depending on the device vendor.
 : Differences in BLE (Bluetooth Low Energy) performance and behavior.
 : While iOS provides consistent and stable Bluetooth performance by controlling both the hardware and the OS, Android chipset and software stacks vary by manufacturer.
 
 
Task 3:
Write between 05-10 high-value test scenarios for this feature.
 - Verify that mode changes in the app are reflected in the hardware within 2 seconds.
 - Confirm that the last configured mode is automatically applied when the earbuds are reconnected after being disconnected.
 - Check if the last settings are maintained even after the app is force-closed and restarted.
 - Verify that mode switching is blocked and a notification message is displayed when the earbud battery is below 5%.
(Test cases: Left/Right at ≥5% and <5% respectively).
 - Ensure that the actual battery levels of the earbuds (Left/Right) and the case are accurately reflected in the app UI in real-time.
 - Confirm that mode-change buttons within the app are disabled when the earbuds are not connected.
 - Verify that the same user experience is provided when the identical scenarios are performed on both iOS and Android.
 - Check if the settings are maintained when changing modes during music playback, taking a call, and then returning to the music.


Task 4:
Write at least 2 detailed test cases in a standard format

Case 1) Automatic Restoration of Last Selected Mode upon Reconnection
- Test Objective: Verify that the previously configured listening mode is automatically restored when the user reconnects the device.
- Preconditions: Earbuds are paired with the mobile device and connected to the app.
- Test Steps:
1. Launch the app and select 'Noise Canceling (NC)' mode.
2. Place the earbuds in the charging case and close the lid to disconnect them.
3. Wait for 10 seconds, then remove the earbuds and reconnect them to the device.
4. Check the listening mode status on the app's main screen. Wear the earbuds to verify the actual operating mode.
- Expected Result: The app UI must display 'Noise Canceling' as active, and noise canceling must be functioning on the actual hardware.

Case 2) Pause/Resume when Receiving/Ending a Call During Music Playback
- Test Objective: Verify that music playback correctly pauses and resumes when a call is received and ended.
- Preconditions: Earbuds are paired with the mobile device and music is currently playing.
- Test Steps:
1. Confirm that music is playing normally on the smartphone connected to the earbuds.
2. Verify that music playback pauses immediately when an incoming call is received.
3. Confirm if music resumes automatically after ending the call (When 'Auto-resume after call' is enabled).
4. Confirm if music remains paused after ending the call, and resumes correctly when manual playback is initiated (When 'Auto-resume after call' is disabled).
- Expected Result: Music playback must correctly pause and resume/remain paused before and after the call.

Task 5:
During testing, you observe the following issue:

- The user selects Transparency Mode in the app while the earbuds are connected. The app immediately updates and shows Transparency Mode as active. However, the earbuds remain in Noise Cancellation for around 8–12 seconds. In some cases, after placing the earbuds back in the case and reconnecting, the app still shows Transparency Mode, but the earbuds are actually in Noise Cancellation Mode.
Write a bug report as you would submit it to the development team.

- Defect Title: [State Mismatch] Synchronization latency between App UI and hardware mode, and state asynchrony upon reconnection.
- Severity: Major
- Priority: High
- Test Environment: Samsung Galaxy 25, Android 14, App v0.0.0, Earbuds Firmware v0.0.0

[Description]
When selecting 'Transparency' mode in the app, the UI updates immediately, but it takes 8–12 seconds for the change to be reflected in the actual earbuds (Requirement: within 2 seconds). Additionally, upon reconnection, a mismatch occurs where the app UI displays the last saved setting, but the hardware defaults to 'Noise Canceling' mode.

[Steps to Reproduce]
1. Connect the earbuds and confirm the 'Noise Canceling' state in the app.
2. Select 'Transparency' mode within the app.
3. Observe the immediate UI change and measure the time it takes for the actual audio mode to switch.
4. Place the earbuds in the case and remove them again to reconnect.
5. Compare the mode displayed in the app with the actual audio output from the earbuds.

[Actual Results]
: Mode Switching Response Time: Approximately 8–12 seconds (Exceeds requirement).
: Upon Reconnection: The app displays 'Transparency,' but the earbuds operate in 'Noise Canceling' mode.

[Expected Results]
: All mode transitions must be completed within 2 seconds.
: The App UI and hardware state must remain synchronized under all circumstances.


Task 6:
Describe how you would explore this feature beyond scripted testing. Please include the kinds of real-world situations you would investigate for headphones/earbuds.

정해진 시나리오 외에 다음과 같은 실생활 시나리오를 탐색합니다.
1. Verify if mode-switching commands are lost or delayed in environments with heavy 2.4GHz signal congestion, such as subway stations or crowded cafes.
2. Confirm that passing through EAS (Electronic Article Surveillance) gates in retail stores does not cause permanent disconnection or malfunction, even if temporary interference occurs.
3. When connected to two devices simultaneously, verify how the display and actual behavior on the second device change when the mode is switched from the app on the first device.
4. Check the exception handling when Bluetooth is forcibly disabled or the earbuds are placed in the case while a mode-switching command is in progress.
5. Verify if the mode switches normally when only one earbud is removed, and check the system response when app control is attempted in that state.
6. Attempt to change the mode during music playback or a voice call to check for any audio glitches, such as popping noises.


Task 7:
Assume these issues were found near release:

- On Android, listening mode changes sometimes take 4 seconds instead of 2 seconds
- On iOS, the battery-low warning is present, but the wording is confusing
- In 1 out of 25 reconnect attempts, the app restores the previous mode visually, but the earbuds actually reconnect in a different mode
Would you recommend: release, conditional release, or no release? Explain your reasoning.


Conditional release or No Release: It depends on the customer's needs

These issues are highly detrimental to premium brand value and user trust.
- State Asynchrony (Critical): The mismatch between the UI and actual hardware, occurring approximately once every 25 attempts, is a severe reliability flaw. Users may experience confusion—such as believing Noise Canceling is on when it is actually off—which is highly likely to lead to the perception of a defective product.
- Response Time Failure (Android): A response time of 4 seconds when the target is 2 seconds does not meet "premium" performance standards. This risks providing a subpar, discriminatory experience specifically for Android users.
- Usability Confusion (iOS): While the ambiguity of the battery warning message may seem minor, when combined with the two technical flaws above, it creates an overall impression of low software quality.

Conclusion:
- Should the client prioritize an early launch despite these defects, I recommend addressing the reconnection state asynchrony issue as the highest priority for the initial release. Subsequently, a follow-up update should be released and verified only after completing Android performance optimization and correcting the iOS messaging.
- Otherwise, no release this time and release after fixing all issues.


<<< Assignment 2: >>>
In the provided Wireshark trace of a Bluetooth audio streaming session between a headset and a smartphone. The user reports audio cuts after a few seconds. 
Provide step-by-step approach on how you would analyze the issue? 

1. Identify Connection Stability and Signal Strength
The first step is to check if the physical link is maintaining adequate signal strength (RSSI).
- Action: Search for [LC][ActiveLink] entries to monitor RSSI.  
- Observation: The log shows RSSI values fluctuating between -46 and -50 dBm (e.g., SmartPhone idx:3, Rssi: -46).  
- Deduction: Since values above -60 dBm are generally considered excellent for Bluetooth, the audio cuts are likely not caused by a weak signal or the devices being too far apart.  

2. Analyze Coexistence and Interference (Adaptive Frequency Hopping)
Bluetooth and Wi-Fi both operate on the 2.4 GHz band. Interference often triggers frequent "Channel Map" changes.
- Action: Examine the [GCS] (Global Coexistence System) logs, specifically Channel Map Change and WiFi Estimate.  
- Observation:
: The log reports a Wi-Fi detection at CH=6 with an RSSI of -84 dBm.  
: There are repeated Channel Map Change suggestions (e.g., from Current[40FF...] to Suggest[7C11...]).  
- Deduction: The system is frequently recalculating which frequencies to avoid. If these changes are too aggressive or fail to sync between the phone and headset, it can cause momentary audio drops.  

3. Check for Scheduling Conflicts or Collisions
Bluetooth audio requires strict timing. If other tasks (like page scanning or BLE background tasks) conflict with the audio stream, packets will be dropped.
Please refer to the contents of the file: A2DP_audio_drops.7z

- Action: Look at the [LC] Scheded entries to see if collisions are occurring.  
- Observation: The log shows Collision:0 in several snapshots, but "Critical Assert" counts for BT/Sniff/eSCO are present (ranging from 8 to 10).  
- Deduction: While collisions are not currently being reported as high, the frequent switching between Standby and Suspend states (over 3,000 times in some intervals) suggests high processor overhead that might jitter the audio timing.  

4. Monitor System Resources (Memory and CPU)
Audio processing (A2DP) requires consistent memory and CPU availability.
- Action: Check [MEMORY_MONITOR] and MCU_perf entries.  
- Observation:
 Memory: The sysram heap free size is steady at 6180.  
 CPU: MCU_perf idle_ratio is 93.96%, and DSP_perf sleep_time is 99.99%.  
- Deduction: The system is mostly idle. The audio cuts are not due to a memory leak or the CPU being pinned at 100%.  

5. Final Step: Correlate Timestamp with Protocol Events
If the issue persists, I would correlate the exact second the user hears a "cut" with the BTTIMER and BTGAP events.
- Observation: There is a specific entry: [TIMER] timer expired!!!!, timer id == 0x1000ffff followed by [GAP] enter bt_gap_connection_sniff_timeout().  
- Conclusion: This indicates a Sniff Mode timeout. The headset is trying to enter a low-power state (Sniff), but if it loses synchronization during this transition, the audio stream will break. I would focus the investigation on why the Sniff transition is failing or timing out during active music playback.

<<< Assignment 3: >>>
The attached zip file TWS_User_Scenario_EXT.7z contains Wireshark logs for a TWS Bluetooth audio system. - Analyse the logs and find out the roles of each device - Find out the primary user scenario covered in the logs - Explain the analysis steps.

- Device1: SmartPhone (iPhone17 pro)
- Device2: Master Earbud
- Device3: Slave Earbud

<Device Role Analysis (Device 1, 2, 3)>
The identity and function of each device can be defined through the address information and communication patterns within the logs:  

Device 1: Smartphone (iPhone17 pro)
Evidence: Logs such as [LC][Client] SmartPhone Rssi: -62 appear repeatedly.  
Role: Acts as the audio source device, transmitting A2DP data to the earbuds and serving as the primary target for RSSI (signal strength) management.  

Device 2: Master Earbud
Evidence: This device acts as the main subject of the logs, directly processing and recording Prox data (wear detection), IMU data (accelerometer), and battery_management.  
Role: Maintains a direct connection (ACL Conn) with the smartphone and serves as the central hub for synchronizing data with the other earbud via AWS (Airoha Wireless Stereo).  

Device 3: Slave Earbud
Evidence: Specifically referred to as "Partner" in logs like @@@ Partner RX_BT3_MIC_ERROR and PartnerLost.  
Role: Receives audio data or shares microphone data with the Master earbud and maintains synchronization status with the primary unit.  

<Primary User Scenario: Wearing Status Monitoring During Music Playback>
The overarching scenario captured in these logs is "a user listening to high-quality music while the system monitors the wearing state of the TWS earbuds".  
- Audio Streaming: Information such as [A2DP] BitRate 186 kbits/s and Samplerate (kHz): 48 confirms that high-fidelity audio is currently playing.  
- Wear Detection & Monitoring: The APP_WEAR_DETECT module continuously checks Prox data (proximity sensor) and IMU data (motion) to monitor whether the user is wearing the device.  
- System Stability Checks: The system performs real-time monitoring of battery levels (soc[88]), internal temperature (temp[35]), and potential feedback issues (Howling FB state: 0).  

<Log Analysis Steps>
1. Environment Identification: Confirmed the hardware identity by identifying the chipset tool (AB1585/88 Logging Tool) and the timestamp (February 2026) from the log headers.  
2. Audio Status Verification: Used the beo_audio_awe_layout_info logs to verify the audio engine status (AudioIsStarted:1), sampling rate, and channel configuration.  
3. Connectivity & Sync Analysis: Analyzed PKA_LOG_LC and AWSCTL logs to check signal strength (RSSI) with the smartphone and the synchronization state (AWS ConnMode) between the earbuds.  
 : Notably, recurring Partner RX_BT3_MIC_ERROR logs indicate intermittent errors in microphone data transmission between the left and right earbuds.  
4. Sensor Data Mapping: Analyzed APP_WEAR_DETECT and BEO_APP_IMU logs to see how physical user actions (wearing status, head movement) are reflected in the system.  
5. Event Tracking: Tracked the flow of internal system events and command receptions via aws_mce_report and ui_shell_send_event found at the end of the logs.
