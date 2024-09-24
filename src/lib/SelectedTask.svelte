<script>
    export let tasks = [];
    export let selectedTask = {};

    function completeTask() {
        selectedTask.done = true;
        tasks[selectedTask.id - 1] = selectedTask;
        tasks = tasks;
        selectedTask = null
    }

    function editTask() {
        tasks[selectedTask.id - 1] = selectedTask;
        tasks = tasks;
    }

    function undoTask() {
        selectedTask.done = false;
        tasks[selectedTask.id - 1] = selectedTask;
        tasks = tasks;
    }

</script>

<div class="selected-task-container">
    <h1 class="title">Selected Task</h1>
    <button class="close-button" on:click={() => {selectedTask = null;}}>X</button>
    <div class="input-container">
        <input
            type="text"
            class="task-name"
            name="task-name"
            placeholder="Task Name"
            bind:value={selectedTask.name}
        />
        <textarea
            class="task-description"
            name="task-description"
            placeholder="Task Description"
            bind:value={selectedTask.description}
            rows="2"
        />
        <input type="number" class="task-time" name="task-time" placeholder="Time spent in minutes" bind:value={selectedTask.minutes}/>
        <textarea
            class="task-description"
            name="task-essay"
            placeholder="What did you learn or accomplish?"
            bind:value={selectedTask.essay}
            rows="10"
        />
    </div>
    <div class="button-container">
        {#if (selectedTask.minutes != null && selectedTask.essay != null && !selectedTask.done)}
        <button type="button" class="complete-button" on:click={completeTask}>Complete</button>
        <button type="button" class="edit-button" on:click={editTask}>Edit</button>
        {:else if (selectedTask.done)}
        <button type="button" class="undo-button" on:click={undoTask}>Undo</button>
        <button type="button" class="edit-button" on:click={editTask}>Edit</button>
        {:else}
        <button type="button" class="complete-button-disabled" on:click={completeTask} disabled>Complete</button>
        <button type="button" class="edit-button" on:click={editTask}>Edit</button>
        {/if}
    </div>
</div>

<style>
    .selected-task-container {
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        border-color: rgb(78, 78, 78);
        border-style: solid;
        border-radius: 10px;
        background-color: #ffffff;
    }

    .title {
        font-size: x-large;
    }

    .close-button {
        position:absolute;
        right: 0;
    }

    .input-container {
        display: flex;
        flex-direction: column;
        padding: 0 3.2rem 1rem;
    }

    .task-name {
        font-size: large;
        padding: 5px;
        margin-bottom: 1rem;
        border-radius: 5px;
    }

    .task-description {
        font-size: large;
        margin-bottom: 1rem;
        border-radius: 5px;
    }

    .task-time {
        font-size: larger;
        margin-bottom: 1rem;
    }

    .button-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-between;
    }

    .complete-button-disabled {
        background-color: #61806a;
        border-radius: 10px;
        border: 1px solid #326637;
        display: inline-block;
        font-size: large;
        color: #000000;
        padding: 10px 2rem;
        text-decoration: none;
        margin-bottom: 1rem;
    }

    .edit-button {
        background-color: #68e1ff;
        border-radius: 10px;
        border: 1px solid #1d74ad;
        display: inline-block;
        font-size: large;
        cursor: pointer;
        color: #000000;
        padding: 10px 2rem;
        text-decoration: none;
        margin-bottom: 1rem;
    }

    .undo-button {
        background-color: #ff6868;
        border-radius: 10px;
        border: 1px solid #ad1d1d;
        display: inline-block;
        font-size: large;
        cursor: pointer;
        color: #000000;
        padding: 10px 2.5rem;
        text-decoration: none;
        margin-bottom: 1rem;
    }

    .complete-button {
        background-color: #68ff95;
        border-radius: 10px;
        border: 1px solid #00a70e;
        display: inline-block;
        font-size: large;
        cursor: pointer;
        color: #000000;
        padding: 10px 2.5rem;
        text-decoration: none;
        margin-bottom: 1rem;
    }
    .complete-button:hover {
        background-color: #81b5f5;
        color: white;
    }
    .complete-button:active {
        position: relative;
        top: 1px;
    }
</style>
