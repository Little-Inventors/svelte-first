<script>
    export let userName;
    export let userImage;
    export let userDescp;
</script>

<div class="card">
    <header>
        <!-- <div
            class={userImage ? "thumbnail" : "thumbnail thumbnail-placeholder"}
        > -->
        <div class="thumbnail" class:thumbnail-placeholder={!userImage}>
            <img src={userImage} alt={userName} />
        </div>
        <div class="user-data">
            <h1>{userName}</h1>
        </div>
    </header>
    <div class="user-data">
        <p>{userDescp}</p>
    </div>
</div>

<style>
    .card {
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
        max-width: 30rem;
        border-radius: 5px;
        margin: 1rem 0;
    }
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .thumbnail {
        width: 33%;
        height: 100%;
    }
    .thumbnail-placeholder {
        background: #ccc;
    }
    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
    .user-data {
        width: 67%;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
</style>
