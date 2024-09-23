<script>
    export let tasks = [];
    export let selectedTask;

    function selectTask(task) {
        selectedTask = task;
    }
</script>

<div class="todo-list">
    <h1 class="title">TO-DO LIST</h1>
    {#each tasks as task}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- svelte-ignore a11y-no-static-element-interactions -->
        <div
            class="todo-item {task.done ? 'done' : ''}"
            on:click={() => selectTask(task)}
            style="background-color: {task === selectedTask
                ? '#8a8a8a'
                : '#e0e0e0'}; color: {task === selectedTask
                ? '#fff'
                : '#000'}"
        >
            <span class="task-name">{task.name}</span>
        </div>
    {/each}
</div>

<style>
    .todo-list {
        background-color: #fff;
        padding: 10px;
        border: 2px solid black;
        border-radius: 10px;
    }
    
    .title {
        margin-top: 0;
        text-align: center;
        font-size: x-large;
    }

    .todo-item {
        padding: 5px 15rem 5px 5px;
        cursor: pointer;
        margin-bottom: 5px;
        border-radius: 5px;
    }

    .task-name {
        font-size: large;
    }

    .todo-item.done {
        text-decoration: line-through;
        color: green;
    }
</style>
