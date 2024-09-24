<script>
    export let dayData;
    let selectedMood; // Variable to track the selected mood

    $: selectedMood = dayData.feeling;

    // Function to handle mood selection
    function setMood(mood) {
        selectedMood = mood;
        dayData.feeling = mood;
        dayData = dayData;
    }
</script>

<div class="container">
    <h2>How are you feeling today?</h2>
    
    <div class="mood-container">
        <!-- Bad Mood SVG -->
        <div class="mood {selectedMood === 'bad' ? 'selected-bad' : ''}" on:click={() => setMood('bad')}>
            <svg viewBox="0 0 100 100" width="80" height="80">
                <circle cx="50" cy="50" r="45" stroke="black" stroke-width="2" fill="none" />
                <line x1="30" y1="35" x2="40" y2="45" stroke="black" stroke-width="3" />
                <line x1="40" y1="35" x2="30" y2="45" stroke="black" stroke-width="3" />
                <line x1="70" y1="35" x2="60" y2="45" stroke="black" stroke-width="3" />
                <line x1="60" y1="35" x2="70" y2="45" stroke="black" stroke-width="3" />
                <path d="M 30 70 Q 50 55 70 70" stroke="black" stroke-width="3" fill="none" />
            </svg>
            <div class="label">Bad</div>
        </div>

        <!-- Neutral Mood SVG -->
        <div class="mood {selectedMood === 'neutral' ? 'selected-neutral' : ''}" on:click={() => setMood('neutral')}>
            <svg viewBox="0 0 100 100" width="80" height="80">
                <circle cx="50" cy="50" r="45" stroke="black" stroke-width="2" fill="none" />
                <circle cx="35" cy="40" r="5" fill="black" />
                <circle cx="65" cy="40" r="5" fill="black" />
                <line x1="30" y1="65" x2="70" y2="65" stroke="black" stroke-width="3" />
            </svg>
            <div class="label">Neutral</div>
        </div>

        <!-- Good Mood SVG -->
        <div class="mood {selectedMood === 'good' ? 'selected-good' : ''}" on:click={() => setMood('good')}>
            <svg viewBox="0 0 100 100" width="80" height="80">
                <circle cx="50" cy="50" r="45" stroke="black" stroke-width="2" fill="none" />
                <circle cx="35" cy="40" r="5" fill="black" />
                <circle cx="65" cy="40" r="5" fill="black" />
                <path d="M 30 60 Q 50 75 70 60" stroke="black" stroke-width="3" fill="none" />
            </svg>
            <div class="label">Good</div>
        </div>
    </div>
</div>

<style>
    .container {
        text-align: center;
        margin-top: 40px;
    }

    .mood-container {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 30px;
        margin: 20px 0;
    }

    .mood {
        cursor: pointer;
        transition: transform 0.2s ease;
        border-radius: 50%;
        padding: 10px;
        background-color: transparent; /* Default background for unselected */
    }

    .mood:hover {
        transform: scale(1.2); /* Slight zoom effect on hover */
    }

    .label {
        text-align: center;
        font-size: 18px;
        font-family: Arial, sans-serif;
    }

    /* Specific background colors when selected */
    .mood.selected-bad {
        background-color: #ff9e9e;
    }

    .mood.selected-neutral {
        background-color: #a8a8a8;
    }

    .mood.selected-good {
        background-color: #6cff6c;
    }

    /* For the SVG icons, let's apply different color styles for better contrast */
    svg {
        width: 100%;
        height: 100%;
    }

    line, circle, path {
        stroke: black;
        stroke-width: 2;
    }
</style>