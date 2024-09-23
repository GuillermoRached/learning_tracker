<script>
    export let percentage = 0; // THis should be between 0 - 100
    // Maybe add a validating function here
</script>

<div class="progress-container">
    <div class="progress-fill" style="--percentage: {percentage}%"></div>
    {#if (percentage < 25)}
        <div class="below-25-label" style="--percentage: {percentage}%">{percentage}%</div>
    {:else if (percentage == 100)}
        <div class="completed-label" style="--percentage: {percentage}%">{percentage}%</div>
    {:else}
        <div class="progress-label" style="--percentage: {percentage}%">{percentage}%</div>
    {/if}
</div>


<style>
    .progress-container {
        width: 300px;
        height: 30px;
        background-color: #e0e0e0;
        border-radius: 15px;
        position: relative;
        overflow: hidden;
        margin: 20px 0;
    }

    .progress-fill {
        background-color: #4caf50;
        height: 100%;
        width: var(--percentage);
        transition: width 0.3s;
        border-radius: 15px 0 0 15px; /* Rounded corners only on the left */
        position: absolute;
    }

    .progress-label {
        position: absolute;
        top: 0;
        left: calc(var(--percentage) - 50px); /* Adjust label position */
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        color: white;
        width: 50px;
        transition: left 0.3s;  /* Smooth transition as percentage changes */
    }
    
    .below-25-label {
        position: absolute;
        top: 0;
        left: max(calc(var(--percentage) - 42px), -10px); /* Adjust label position */
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        color: white;
        width: 50px;
        transition: left 0.3s;  /* Smooth transition as percentage changes */
    }

    .completed-label {
        position: absolute;
        top: 0;
        left: 45%; /* Adjust label position */
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        color: white;
        width: 50px;
        transition: left 0.3s;  /* Smooth transition as percentage changes */
    }
</style>