<script>
    export let days;
    export let currentDay;

    let menuOpen = false; // Toggle for the menu's open state

    function toggleMenu() {
        menuOpen = !menuOpen;
    }

    function selectDay(index) {
        currentDay = index;
        menuOpen =  false
    }
</script>

<div class="hamburger-menu {menuOpen ? "open" : ""}" on:click={toggleMenu}>
    <svg viewBox="0 0 30 30">
        <line x1="5" y1="8" x2="25" y2="8"></line>
        <line x1="5" y1="15" x2="25" y2="15"></line>
        <line x1="5" y1="22" x2="25" y2="22"></line>
    </svg>
</div>

<!-- Sliding menu -->
<div class="menu {menuOpen ? 'open' : ''}">
    {#each days as day, index}
        <div class="menu-item" on:click={() => selectDay((days.length - 1) - index)}>{day.toDateString()}</div>
    {/each}
</div>

<style>
    /* Positioning the hamburger menu in the top-left corner */
    .hamburger-menu {
        position: absolute;
        top: 20px;
        left: 20px;
        width: 35px;
        height: 35px;
        cursor: pointer;
        z-index: 3; /* Ensure it's above everything */
        transition: left 0.3s ease, top 0.3s ease; /* Animate both top and left properties */
    }

    /* When the menu is open, move the hamburger menu icon to the top-right */
    .hamburger-menu.open {
        left: calc(30vw - 55px); /* Move to the right edge of the menu (25vw) minus the width of the icon */
        top: 20px;
    }

    svg {
        width: 100%;
        height: 100%;
    }

    line {
        stroke: #000; /* Black lines for the hamburger icon */
        stroke-width: 4;
        stroke-linecap: round;
    }

    /* Sliding menu */
    .menu {
        position: fixed;
        top: 0;
        left: 0;
        width: 25vw; /* Half of the screen width */
        height: 100vh; /* Full height of the screen */
        background-color: #333; /* Dark background for the menu */
        color: white;
        transform: translateX(-100%); /* Initially hide the menu off the screen */
        transition: transform 0.3s ease; /* Smooth slide-in effect */
        z-index: 1; /* Behind the hamburger icon */
        display: flex;
        flex-direction: column;
        align-items: start;
        padding: 20px;
    }

    .menu.open {
        transform: translateX(0); /* Slide the menu in when open */
    }

    .menu-item {
        margin: 15px 0;
        font-size: 18px;
        cursor: pointer;
    }
</style>