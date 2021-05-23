<script>
    import Card from "./Card.svelte";
    let name = "";
    let image = "";
    let descrption = "";
    let formStatus = "empty";
    let createdCard = [];

    function deleteLast() {
        createdCard = createdCard.slice(0, -1);
    }

    function deleteFirst() {
        createdCard = createdCard.slice(1);
    }

    function addCard() {
        formStatus =
            name.trim().length === 0 ||
            image.trim().length === 0 ||
            descrption.trim().length === 0
                ? "invalid"
                : "done";
        if (formStatus === "invalid") return;
        else {
            createdCard = [
                ...createdCard,
                {
                    name: name,
                    image: image,
                    descrption: descrption,
                },
            ];
        }
    }
</script>

<main>
    <div>
        <label for="name"> Name </label>
        <input type="text" bind:value={name} />
        <label for="image"> Image </label>
        <input type="text" bind:value={image} />
        <label for="description"> Descrption </label>
        <input type="text" bind:value={descrption} />
        <br />
        <button on:click={addCard}>Submit</button>
        <button on:click={deleteFirst}>Delete First</button>
        <button on:click={deleteLast}>Detete Last</button>
    </div>

    {#if formStatus === "invalid"}
        <p>Invalid Input</p>
    {/if}

    {#each createdCard as card}
        <Card
            userName={card.name}
            userImage={card.image}
            userDescp={card.descrption}
        />
    {/each}
</main>

<style>
    main {
        width: 66%;
        margin: 10px auto;
    }

    label {
        font-style: italic;
        font-weight: 500;
        padding-top: 1em;
        text-transform: uppercase;
    }
    input {
        width: 30rem;
    }
    input:active,
    input:hover {
        background: wheat;
    }

    button {
        padding: 1rem;
        width: 12%;
        text-transform: uppercase;
        color: wheat;
        background: brown;
    }

    button:hover {
        background: wheat;
        color: brown;
        cursor: pointer;
    }
</style>
