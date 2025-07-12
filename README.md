# Mobile UI Automation with Maestro

This repository contains End-to-End (E2E) UI test automation for a mobile application, developed using the [Maestro](https://maestro.mobile.dev/) framework.

## Project Overview

This project aims to automate user interface interactions and flows for the `TicTac` mobile application. The tests ensure the core functionalities of the application work as expected across different mobile platforms (primarily Android, with potential for iOS).

## Getting Started

To run these tests, you will need to have Maestro CLI installed and a mobile device (physical or emulator) connected and configured for debugging.

### Prerequisites

* **Maestro CLI:** Follow the official installation guide:
    ```bash
    curl -Ls "[https://get.maestro.mobile.dev](https://get.maestro.mobile.dev)" | bash
    ```
    After installation, open a new terminal or run `export PATH="$PATH":"$HOME/.maestro/bin"` and then `maestro -v` to verify the installation.
* **Android Device/Emulator:**
    * Ensure your Android device has **Developer Options** and **USB Debugging** enabled.
    * For a smoother testing experience, it's highly recommended to **disable screen lock (PIN, password, pattern)** and set the **screen timeout to "Never"** or a very long duration on your test device.
    * Install the `TicTac` application on your device via ADB:
        ```bash
        adb install /path/to/your/TicTac.apk
        ```
        (Replace `/path/to/your/TicTac.apk` with the actual path to your application's APK file).

### Running the Tests

1.  **Navigate to the project directory:**
    Open your terminal and change the directory to this project's root:
    ```bash
    cd /path/to/your/Mobile/TicTacMaestro # Adjust this path as needed
    ```
2.  **Execute Maestro tests:**
    To run all tests within the `.maestro/` directory:
    ```bash
    maestro test .maestro/
    ```
    To run a specific test file:
    ```bash
    maestro test .maestro/test.yaml
    ```
    Observe the test execution directly on your connected device/emulator.

## Test Files

All Maestro test flows are located in the `.maestro/` directory.

### `test.yaml`

This file contains the primary E2E test flow for the `TicTac` application.

**`appId: com.serhiiqa.TicTac`**

**Flow Description:**

This test sequence performs the following actions:

1.  **`launchApp`**: Launches the `TicTac` application. (Note: `clearState: true` is omitted due to potential permission issues on some Android devices, meaning the app's state will not be cleared automatically before each run unless manually reset).
2.  **`assertVisible: "Tic Tac Toe"`**: Verifies that the "Tic Tac Toe" title is visible, confirming the app is loaded.
3.  **`tapOn` (multiple points)**: Simulates a sequence of taps on specific screen coordinates to play a game of Tic-Tac-Toe. These taps are designed to lead to a win for Player X.
4.  **`assertVisible: "🏆 Player X wins!"`**: Confirms that the victory message for Player X appears.
5.  **`tapOn: "PLAY AGAIN"`**: Taps the "PLAY AGAIN" button to reset the game.
6.  **`assertVisible: "X: 1 | O: 0"`**: Verifies that the score for Player X has been updated to 1, confirming the game reset and score tracking.

## Related Application Repository

This automation project targets the `TicTac` mobile application. You can find the source code for the application here:

[**TicTac Application Repository**](https://github.com/yourusername/TicTac-App-Repo) ## Technologies Used

<p align="left">
  <img src="https://img.shields.io/badge/Maestro-4D93C3?style=for-the-badge&logoColor=white" alt="Maestro Badge"/>
  <img src="https://img.shields.io/badge/Android%20Studio-3DDC84?style=for-the-badge&logo=android-studio&logoColor=white" alt="Android Studio Badge"/>
</p>