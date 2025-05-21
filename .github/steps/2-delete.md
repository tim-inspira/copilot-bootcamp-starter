### :keyboard: Activity: Adding Item Deletion Functionality

In this exercise, you'll use GitHub Copilot's Agent mode to implement functionality for deleting items from both the frontend and backend of the application.

### What is GitHub Copilot Agent Mode?

**Agent mode** enhances Copilot by providing it a feedback loop, allowing it to:
- Inspect its own results for issues, bugs, and inconsistencies
- Automatically revise its work based on what it discovers
- Handle more complex, multi-step tasks like implementing features across multiple files

### :keyboard: Activity: Use Agent mode to add item deletion functionality

Let's add the ability to delete items from our application. This will require changes to both the backend (adding a DELETE endpoint) and the frontend (adding delete buttons next to each item).

1. Open the **Copilot** chat panel and switch to **Agent** mode using the dropdown menu.

1. Use the following prompt to ask Copilot to implement the delete functionality:

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > I want the ability to delete an item
   > ```

1. Copilot will analyze your codebase and implement:
   - A new DELETE endpoint in the backend
   - Delete buttons next to each item in the frontend
   - Event handlers to connect the buttons to the API

1. When Copilot finishes making the changes, review what was modified:
   - In the backend (`packages/backend/src/app.js`), you should see a new DELETE endpoint
   - In the frontend (`packages/frontend/src/App.js`), you should see delete buttons added next to each item

1. If it's not already running, run the application with `npm run start` in the root directory to test the new functionality.

1. Try deleting some items to verify everything works as expected.

1. Keep the changes that copilot implemented.

1. Commit and push to the main branch.

### Success Criteria

To complete this exercise successfully:
- The backend should have a DELETE endpoint at `/api/items/:id`
- The frontend should display a delete button next to each item
- Clicking a delete button should remove the item from both the UI and the database

If you encounter any issues, you can:
- Ask Copilot to fix specific problems
- Check the developer console for any errors
- Verify that the DELETE endpoint is properly implemented in the backend