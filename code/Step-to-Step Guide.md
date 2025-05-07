# Step-by-Step Guide: Building the Steps Recorder App in MIT App Inventor

This guide provides instructions on how to construct the Simple Steps Recorder application using MIT App Inventor, based on the provided screenshots.

## Step 1: Project Setup

1.  Navigate to the MIT App Inventor website (appinventor.mit.edu) and log in.
2.  Click **Projects** > **Start new project**.
3.  Enter the project name `Steps Recorder` and click **OK**.

## Step 2: Designing the User Interface (Designer View)

Switch to the **Designer** view.

1.  **Add Status Label:**
    * From the **Palette** > **User Interface**, drag a **`Label`** onto the Viewer.
    * Select the `Label`.
    * In the **Properties** pane, set **`Text`** to `You have not done any steps right now.`.
    * *Optional but Recommended:* Rename the component to `StatusLabel`.

2.  **Add Start Button:**
    * From the **Palette** > **User Interface**, drag a **`Button`** onto the Viewer.
    * Select the `Button`.
    * In Properties, set **`Text`** to `Start`.
    * Set **`Width`** to `Fill parent`.
    * *Optional:* Rename to `StartButton`.

3.  **Add Steps Display Label:**
    * From the **Palette** > **User Interface**, drag a **`Label`** onto the Viewer.
    * Select the `Label`.
    * In Properties, set **`Text`** to `0`.
    * Set **`FontBold`** to `true` (optional, for emphasis).
    * Set **`TextAlignment`** to `Center`.
    * *Optional:* Rename to `StepsLabel`.

4.  **Add Stop Button:**
    * From the **Palette** > **User Interface**, drag a **`Button`** onto the Viewer.
    * Select the `Button`.
    * In Properties, set **`Text`** to `Stop`.
    * Set **`Width`** to `Fill parent`.
    * *Optional:* Rename to `StopButton`.

5.  **Add Reset Button:**
    * From the **Palette** > **User Interface**, drag a **`Button`** onto the Viewer.
    * Select the `Button`.
    * In Properties, set **`Text`** to `Reset`.
    * Set **`Width`** to `Fill parent`.
    * *Optional:* Rename to `ResetButton`.

6.  **Add Non-visible Components:**
    * From the **Palette** > **Sensors**, drag a **`Pedometer`** component onto the Viewer. It will appear in the "Non-visible components" area below the screen.
    * From the **Palette** > **Media**, drag a **`TextToSpeech`** component onto the Viewer. It will also appear in the "Non-visible components" area.

Your Designer view should now contain the labels, buttons, and the non-visible components as shown in the screenshot.

## Step 3: Programming the App Logic (Blocks Editor)

Click the **Blocks** button in the top right corner to switch to the Blocks Editor.

1.  **Start Button Logic:**
    * Click on `StartButton` (or your renamed button) in the Blocks pane on the left. Drag out the **`when StartButton.Click do`** block.
    * Inside this block:
        * Click on `Pedometer1`. Drag out the **`call Pedometer1.Start`** block.
        * Click on `StatusLabel`. Drag out the **`set StatusLabel.Text to`** block.
        * Click on **Built-in** > **Text**. Drag out a **`text`** block (with empty quotes). Type `Walk as much you can. Good luck` inside the quotes. Snap this into the `set StatusLabel.Text` block.
        * Click on `TextToSpeech1`. Drag out the **`call TextToSpeech1.Speak message`** block.
        * Click on **Built-in** > **Text**. Drag out a **`text`** block. Type `Walk as much you can;` inside the quotes. Snap this into the `message` socket.

2.  **Stop Button Logic:**
    * Click on `StopButton`. Drag out the **`when StopButton.Click do`** block.
    * Inside this block, click on `Pedometer1`. Drag out the **`call Pedometer1.Stop`** block.

3.  **Reset Button Logic:**
    * Click on `ResetButton`. Drag out the **`when ResetButton.Click do`** block.
    * Inside this block:
        * Click on `Pedometer1`. Drag out the **`call Pedometer1.Reset`** block.
        * Click on `StepsLabel`. Drag out the **`set StepsLabel.Text to`** block.
        * Click on **Built-in** > **Math**. Drag out a **`number`** block (with `0`). Snap this into the `set StepsLabel.Text` block.

4.  **Pedometer Step Events:**
    * Click on `Pedometer1`. Drag out the **`when Pedometer1.SimpleStep simpleSteps distance do`** block.
    * Inside this block:
        * Click on `StepsLabel`. Drag out the **`set StepsLabel.Text to`** block.
        * Hover over the `simpleSteps` variable in the `SimpleStep` block header, select **`get simpleSteps`**, and snap it into the `set StepsLabel.Text` block.

    * Click on `Pedometer1` again. Drag out the **`when Pedometer1.WalkStep walkSteps distance do`** block.
    * Inside this block:
        * Click on `StepsLabel`. Drag out the **`set StepsLabel.Text to`** block.
        * Hover over the `walkSteps` variable in the `WalkStep` block header, select **`get walkSteps`**, and snap it into the `set StepsLabel.Text` block.
        * *Note:* The screenshot shows both `SimpleStep` and `WalkStep` updating the same label (`Label2` which we called `StepsLabel`). In a real app, you might choose to display either simple steps or walking steps, or perhaps both in different labels. This implementation follows the screenshot directly.

Arrange your blocks neatly in the workspace. Your blocks should now look similar to the screenshot provided.

## Step 4: Testing the Application

1.  In the App Inventor web interface, click **Connect** in the top menu.
2.  Choose your preferred testing method:
    * **AI Companion:** Use the MIT AI2 Companion app on an Android device. Scan the QR code provided.
    * **Emulator:** Launch an Android emulator connected to App Inventor (ensure it supports sensor simulation).
3.  Test the application on your device or emulator. Tap **Start**, move around to trigger the pedometer, verify the step count updates, and test the **Stop** and **Reset** buttons.

You have successfully built the Steps Recorder application!
