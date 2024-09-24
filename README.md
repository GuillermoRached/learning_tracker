# Learning Growth Tracker

## Overview
The **Learning Growth Tracker** is a journaling application designed to help users track their tasks, reinforce learning, and monitor personal growth over time. The application allows users to add tasks, mark them as complete, and reflect on the learning experience. Each completed task requires the user to input the time spent and a small reflective essay. Additionally, users can view and edit previous entries, making it a comprehensive learning tool.

## Features
1. **Task Management**:
   - Add new tasks with a description and name.
   - View a to-do list that shows both active and completed tasks.
   - Mark tasks as done by entering the time spent and a reflective essay.

2. **Progress Tracking**:
   - Track progress with a dynamic progress bar that adjusts based on completed tasks.
   - Easily review progress made during a single session and track over time.

3. **Mood Tracker**:
   - At the end of each session, users can input how they are feeling using mood icons (`Bad`, `Neutral`, `Good`).
   - The mood tracker allows the user to associate their emotional state with their learning experience.

4. **Editable Entries**:
   - All entries can be reviewed and edited, allowing users to reflect back on previous days.
   - Journaling is organized by date, with easy access to past entries and stats about daily productivity.

## How to Use

### 1. Add a Task
- **Step 1**: In the top-right panel, enter a new task by filling out the **Task Name** and **Task Description** fields.
- **Step 2**: Click the "Add" button. The task will be added to your **To-Do List** in the middle of the page.

### 2. Complete a Task
- **Step 1**: When you've finished a task, click on it in the **To-Do List**.
- **Step 2**: The task will open in a detailed panel where you can write a reflection and input the minutes spent.
- **Step 3**: Click "Complete". This will mark the task as done and move it to the completed section.

### 3. Record Reflection
- Each completed task requires a reflective essay to reinforce learning. When you complete a task, input your reflection in the provided text area.
- This journal will help users learn from their completed tasks, making it easier to recall and retain the knowledge gained.

### 4. Track Mood
- **Step 1**: At the bottom of the interface, choose how you feel after completing your tasks by selecting one of the three mood icons: **Bad**, **Neutral**, or **Good**.
- **Step 2**: Your mood will be saved for each session and associated with your performance on that day.

### 5. View Past Entries
- Use the date picker (once implemented) to navigate through past days, review your previous tasks, and reflect on your overall growth.

## Color Scheme
The color scheme has been chosen to enhance readability and support emotional cues:
- **Task Completed**: Light green background indicates completion.
- **Bad Mood**: Red background when selected.
- **Neutral Mood**: Gray background when selected.
- **Good Mood**: Green background when selected.
- **Add Button**: Soft blue for a friendly, noticeable action button.
- **Progress Bar**: Gradient green showing growth and success.

## Technologies Used
- **Frontend**: 
  - **Svelte**: A lightweight framework for building fast and interactive user interfaces.
  - **JavaScript**: For logic handling and interaction.
  - **CSS**: For layout and styling of the components.

## Future Enhancements
1. **Analytics Dashboard**: Visualize productivity over time, track how much time is spent per task category, and analyze learning trends.
2. **Task Categories**: Add tags or categories to tasks (e.g., work, personal, study) for better organization.
3. **Date Navigation**: Allow users to browse through historical data by selecting dates, providing them with insights into their growth.
4. **Customizable Themes**: Users can choose from a variety of color schemes based on personal preference.

## Installation

### Prerequisites
- **Node.js** and **npm** installed.

### Steps
1. Clone the repository

2. Install the dependencies:
   ```bash
   npm install
   ```

3. Run the development server:
   ```bash
   npm run dev
   ```

4. Open your browser and navigate to `http://localhost:5173` to view the application.

## Contributing
We welcome contributions! Feel free to fork the repository and submit a pull request with enhancements, bug fixes, or new features.

## Contact
For any issues or feature requests, feel free to open an issue on GitHub or contact the developer:

- Email: guillermorached@hotmail.com
- GitHub: [GuillermoRached](https://github.com/GuillermoRached)
