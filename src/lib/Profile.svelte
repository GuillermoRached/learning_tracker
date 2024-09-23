<script>
    export let user;

    const today = new Date();
</script>

<div class="profile-container">
    <h1 class="user-name">{user.name ?? "No Name"}</h1>
    <img class="user-image" src={user.imageUrl != "" ? user.imageUrl : "images/calcifer.png"} alt="user" />
    <br/>
    <time>{today.toDateString()}</time>
    <p class="active-days">Active Days: {user.activeDays ?? 0}</p>
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
</style>
