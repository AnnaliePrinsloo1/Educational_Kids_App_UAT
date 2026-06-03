# Test Design: Manual Test Cases Suite

**Project Name:** Educational Kids Neurodevelopment App  
**Methodology Alignment:** ISTQB® Foundation Level v4.0.1  
**Target Hardware Matrix:** Samsung Galaxy S21 FE 5G (Android 16 / One UI 8.0)
**Document Version:** Version 1.2  
**Date:** 2026-05-29  
**Current Lifecycle State:** 🔴 **SUSPENDED / BLOCKED BY ENVIRONMENT** 
*ISTQB Operational Note: This test suite remains pristine and verified against the test basis. However, manual execution of these cases is completely frozen and blocked. Entry Criteria 8.1.1 (Build Delivery) has failed. Refer to `defect_register.md` ID: `BLOCKER-01` for the root cause.*

---

## Test Suite 1: Navigation (NAV)

### TC-NAV-01: Main Menu & Tab Navigation Verification
* **Priority:** High (Core app structure blockers must be caught first)
* **Preconditions:** App is installed and freshly launched (Cold Start). Device navigation gestures/buttons are fully functional.
* **Step-by-step Actions:**
    1. Observe the landing view and primary application dashboard.
    2. Tap the first secondary navigation tab/menu item on the dashboard.
    3. Tap the subsequent structural navigation tab located on the primary navigation bar.
    4. Cycle through all remaining primary dashboard tabs sequentially.
* **Expected Result:** App switches views immediately. Navigation bar updates active states seamlessly with no screen flickering or structural stalls.

### TC-NAV-02: Deep Section Traversal & Back-Button Validation
* **Priority:** High (Ensures users do not get stuck in dead ends while exploring content)
* **Preconditions:** App is running. User is on the main dashboard layout.
* **Step-by-step Actions:**
    1. Select a main menu item to access a primary section.
    2. Tap a nested sub-section component to navigate deeper into the content hierarchy.
    3. Select an individual child entry/detailed view item to reach maximum depth.
    4. Tap the application's built-in top-left back arrow icon to step backward.
    5. Tap the physical Android system back button or execute the One UI system back gesture.
* **Expected Result:** Deep navigation loads correct child elements without performance drops. Back-navigation flows accurately follow the historical stack trail without trapping the user in UI loops or forcing unexpected app exits.

## Test Suite 2: Content Delivery (CON)
### TC-CON-01: High-Accuracy Textual & Asset Rendering
* **Priority:** High (This is a content-driven app for caregiving notes; reading text is vital)
* **Preconditions:** Stable local network connection active on the Samsung S21 FE device.
* **Step-by-step Actions:**
    1. Navigate to the primary educational caregiver resource library section.
    2. Select an educational note containing both text strings and accompanying image graphics.
    3. Rapidly scroll past the top text block down to the base of the file view.
    4. Exit the note, disconnect device data/Wi-Fi, and re-open the same note resource.
* **Expected Result:** Text elements display crisp layout formatting. Images render correctly without placeholder errors or blank states. Offline execution displays cached text safely or serves a friendly system alert rather than throwing a raw null pointer crash.

### TC-CON-02: External Resource Link Redirection Integrity
* **Priority:** Medium (Secondary journey; links must work but don't break local reading if they fail)
* **Preconditions:** Device has a default internet browser selected in Android 16 settings.
* **Step-by-step Actions:**
    1. Open a caregiving resource article that includes hyperlinks to third-party web content.
    2. Tap the highlighted external hyperlink reference text inside the note layout.
    3. Observe the system reaction and transition behavior.
    4. Execute the system back action from the external location to return to the application space.
* **Expected Result:** Tapping the link safely prompts or triggers the external browser engine. The application remains running robustly in the background, keeping its place in the UI stack upon returning.

## Test Suite 3: UI Interactions (UI)
### TC-UI-01: Input Form Field Boundary & Checkbox Compliance
* **Priority:** High (Critical for forms where caregivers input details about their children)
* **Preconditions:** App is open on a caregiving input form view or custom profile configuration screen.
* **Step-by-step Actions:**
    1. Select the primary text input field and enter valid string data.
    2. Attempt to input extreme character boundaries (e.g., paste 500+ string characters or specialized emoji symbols) to stress-test the field box.
    3. Tap all individual checkbox selection items visible on the current profile layout.
    4. Clear the text input completely and attempt to press the submit action button.
* **Expected Result:** Interactive entry boxes reject overflows or truncate excess strings elegantly. Checkboxes toggle cleanly. Empty mandatory forms display descriptive validation hints instead of freezing the UI.

### TC-UI-02: Button & Touch Target Responsiveness
* **Priority:** Medium (Polishes interactive usability across the user interface layout)
* **Preconditions:** Display is clean; touch responsiveness calibration on the Exynos 2100 hardware is normal.
* **Step-by-step Actions:**
    1. Tap closely along the outermost perimeter edge of an interface action button.
    2. Tap closely along the outermost perimeter edge of an interface action button.
    3. Tap adjacent interactive elements in quick succession across the layout boundaries.
* **Expected Result:** Every active asset registers touch accurately within reasonable proximity boundaries. Multi-taps resolve without queuing conflicting UI requests or causing race condition lockups.

## Test Suite 4: Performance (PERF)
### TC-PERF-01: Interface Rendering Stability & Scroll Metrics
* **Priority:** Medium (Focuses on app smoothness; prevents sensory frustration or friction)
* **Preconditions:** Ensure no performance-throttling battery-saver profiles are running on the S21 FE device.
* **Step-by-step Actions:**
    1. Navigate into a highly detailed text section or massive scrollable logging grid view.
    2. Drag your finger downward rapidly to perform an aggressive scroll sweep to the bottom layout edge.
    3. Drag upward instantly to sweep back up to the top layout edge.
    4. Closely watch screen composition for any unexpected visual anomalies or frame drops.
* **Expected Result:** Scrolling runs smoothly with constant refresh frame rates. Text remains clear without tearing, jagged stuttering, or random screen reflow shifts during motion.

## Test Suite 5: Accessibility (ACC)
* **Priority:** High (Essential for diverse caregiver age groups, including elderly users with large-text needs)
* **Preconditions:** Exit app. Go to Android 16 System Settings -> Display -> Font size and style. Set Font Size slider to maximum scale.
* **Step-by-step Actions:**
    1. Relaunch the application build.
    2. Inspect the text alignment and spacing layout across the main dashboard interface.
    3. Navigate through the core caregiver notes sections.
    4. Inspect text presentation on views that feature action confirmation buttons at the base of the UI layout.
* **Expected Result:** All text parameters auto-scale appropriately according to the system configuration. Words reflow cleanly into multi-line configurations without clipping boundaries, overlapping other items, or pushing interaction buttons completely off-screen.

## Test Suite 6: Interruption (INT)
### TC-INT-01: Note Preservation During Active Voice Call Interruption
* **Priority:** Critical (Prevents critical caregiver data loss, matching RISK-02 explicitly)
* **Preconditions:** App is running. Open an entry view and type a half-completed critical sentence inside a note input box.
* **Step-by-step Actions:**
    1. Trigger an incoming mobile voice call or execute a mock background dialer call to interrupt the device state.
    2. Allow the call screen overlay to completely block out the application UI window view for at least 15 seconds.
    3. Terminate or decline the incoming call connection.
    4. Resume the application from the Android 16 recent applications tray view.
* **Expected Result:** The application retains its exact pre-interruption state. The typed draft sentence remains intact within the input form without clearing data or throwing memory management exceptions.

### TC-INT-02: State Retention on Hardware System Interruptions
* **Priority:** High (Maintains app tracking state during typical hardware behaviors)
* **Preconditions:** App is active on a deep content or educational notes screen.
* **Step-by-step Actions:**
    1. Press the hardware Power/Lock button on the physical Samsung S21 FE to lock the screen completely.
    2. Keep the phone device in a locked state for 30 seconds.
    3. Unlock the phone device using biometric verification or PIN authentication passcode.
    4. Trigger a simulated low-battery warning overlay or pull down the quick settings panel shade, then clear it away.
* **Expected Result:** The application recovers instantly from the sleep transition cycle. It retains the exact scroll depth, active tab orientation, and data view state without returning to the boot logo or home screen.