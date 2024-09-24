<script>
    export let dayData;

    let taskList = dayData.tasks

    let newTaskName = "";
    let newTaskDescription = "";

    function addTask() {
        if (newTaskName && newTaskDescription) {
            taskList = [
                ...taskList,
                {
                    id: taskList.length + 1,
                    name: newTaskName,
                    description: newTaskDescription,
                    minutes: 0,
                    done: false,
                },
            ];
            dayData.tasks = taskList;
            dayData = dayData;
            newTaskName = "";
            newTaskDescription = "";
        }
    }
</script>

<div class="new-entry-container">
    <h1 class="title">New Entry</h1>
    <div class="input-container">
        <input
            type="text"
            class="task-name"
            name="task-name"
            placeholder="Task Name"
            bind:value={newTaskName}
        />
        <textarea
            class="task-description"
            name="task-description"
            placeholder="Task Description"
            bind:value={newTaskDescription}
            rows="10"
        />
    </div>
    <button class="add-button" on:click={addTask}>Add</button>
</div>

<style>
    .new-entry-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        border-color: rgb(78, 78, 78);
        border-style: solid;
        border-radius: 10px;
        background-color: #ffffff;
        margin-right: auto;
    }

    .title {
        font-size: x-large;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        padding: 0 3.2rem 3rem;
    }

    .task-name {
        font-size: large;
        padding: 5px;
        margin-bottom: 1rem;
        border-radius: 5px;
    }

    .task-description {
        font-size: large;
        border-radius: 5px;
    }

    .add-button {
        background-color: #c2d8ff;
        border-radius: 10px;
        border: 1px solid #a1b9ff;
        display: inline-block;
        font-size: large;
        cursor: pointer;
        color: #000000;
        padding: 10px 2.5rem;
        text-decoration: none;
        /* text-shadow: 0px 1px 0px #f7f7f7; */
    }
    .add-button:hover {
        background-color: #81b5f5;
        color: white;
    }
    .add-button:active {
        position: relative;
        top: 1px;
    }
</style>
