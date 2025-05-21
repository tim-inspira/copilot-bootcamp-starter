### :keyboard: Activity: Open the project in GitHub Codespaces

Welcome to the Copilot Bootcamp! In this first step, you'll set up your development environment using GitHub Codespaces, which provides a complete, cloud-hosted development environment right in your browser.

### What is GitHub Codespaces?

**GitHub Codespaces** is a cloud development environment that allows you to:
- Code directly in your browser without any local setup
- Access a fully configured Visual Studio Code environment
- Run and test your applications in the cloud
- Work from any device with an internet connection

Having a consistent development environment ensures all bootcamp participants have the same experience, regardless of their local machine setup.

### :keyboard: Activity: Launch a Codespace for this repository

1. Left-click the below button to open the **Create Codespace** page in a new tab. Use the default configuration.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Confirm the **Repository** field is your copy of the exercise, not the original, then click the green **Create Codespace** button.

   - ✅ Your copy: `/{{{full_repo_name}}}`
   - ❌ Original: `/ilan-klinghofer/copilot-bootcamp-starter`

1. Wait a moment for Visual Studio Code to load in your browser.

1. Wait for your codespace to start. This may take a few moments as GitHub sets up a fresh development environment for you.

1. When the codespace is ready, you'll see a Visual Studio Code interface in your browser. This environment includes:
   - All required dependencies pre-installed
   - The project code already cloned and ready to use
   - VS Code extensions needed for the bootcamp pre-configured

1. Explore the environment by opening the Explorer panel (click the files icon in the left sidebar) and navigating through the project structure.

1. You should see a terminal open that is automatically running final setups including 'npm install'. Wait for this to complete.

1. Open a terminal by clicking on **Terminal** in the top menu, then **New Terminal**.

1. Run the following command to start the application:

   ```bash
   npm run start
   ```

1. When the app has started, you should see logs indicating that both the frontend and backend are running.

1. A new browser tab should automatically open up, displaying the React app. If it doesn't, click on the **Ports** tab at the bottom of the window, then click the "Open in Browser" icon (globe icon) for port 3000.

1. You should see the application running in a new browser tab with the title "React Frontend with Node Backend".

### :keyboard: Activity: Use GitHub Copilot Agent Mode to modify the app title

Now, let's use GitHub Copilot's Agent Mode to change the application title:

1. In VS Code, open Github Copilot.

1. At the bottom of the Copilot panel, in the 'Ask Copilot' text box, click on the dropdown menu (next to the send button) and select **Agent** mode.

1. In the same dropdown menu, click the model selector (it might say "GPT-4o" or another model name) and select **Claude 3.7 Sonnet** from the list.
   - *If you don't see a model selector dropdown, first type something into the GitHub Copilot chat to initialize Copilot*

1. In the Copilot chat input field at the bottom of the panel, type the following prompt:
   
   ```
   Change the title of the main screen from "React Frontend with Node Backend" to "Hello World"
   ```

1. Press Enter and allow Copilot Agent to analyze the codebase and make the necessary changes.

1. Once Copilot has completed the changes, refresh the browser tab where the application is running to see the updated title.

1. Review the changes made by Copilot and select 'Keep' for each change, or press the 'Keep' button in the copilot sidebar to accept all changes.

1. Commit and push your changes to the main branch

1. Now that your changes are pushed to GitHub, Mona should already be busy checking your work. Give her a moment and keep watch in the comments. You will see her respond with progress info and the next lesson.

### :bulb: Tip: Making the most of Codespaces

- You can customize your codespace by adjusting VS Code settings
- The terminal is fully functional and supports all standard commands
- Changes are automatically saved to your codespace
- If you close your browser, your codespace will still be available when you return
