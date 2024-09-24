<script>
    export let user;
    export let feelings;
    const today = new Date();
</script>

<div class="profile-container">
    <h1 class="user-name">{user.name ?? "No Name"}</h1>
    <img class="user-image" src={user.imageUrl} alt="user" />
    <br/>
    <time>{today.toDateString()}</time>
    <p class="active-days">Active Days: {user.activeDays ?? 0}</p>
    <div class="day-summary">
        <p>Good Days: {feelings[2]}</p>
        <p>Bad Days: {feelings[0]}</p>
        <p>Everything in between: {feelings[1]}</p>
    </div>
</div>

<style>
    .profile-container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .user-name {
        font-size: xx-large;
        margin-bottom: 1px;
    }

    .user-image {
        border-radius: 50%;
        width: 200px;
    }
    
    .active-days {
        margin-top: 0;
        margin-bottom: 1px;
    }

    .day-summary {
        display: flex;
        flex-direction: column;
        align-items: center;
        font-size: small;
    }

    .day-summary p {
        margin: 0;
    }
</style>
