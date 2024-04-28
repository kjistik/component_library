<script>
    import { onMount } from "svelte";
    export let bars = "/src/lib/icons/bars-solid.svg";
    export let x = "/src/lib/icons/xmark-solid.svg";
    export let divider_color = "#000000";
    export let dropdownList;
    export let image_background_color = "#ffffff";
    export let data_background_color = "blanchedalmond";
    export let data_hover_background_color = "red";
    export let font_size = "15px";
    let flag = false;
    let sameColor = false;
    onMount(() => {
        //🐟
        let variables = document.documentElement.style;
        variables.setProperty(
            "--image-background-color",
            image_background_color,
        );
        variables.setProperty("--divider-color", divider_color);
        variables.setProperty("--data-background-color", data_background_color);
        variables.setProperty(
            "--data-hover-background-color",
            data_hover_background_color,
        );
        variables.setProperty("--font-size-text", font_size);
        sameColor =
            variables.getPropertyValue("--image-background-color") ==
            variables.getPropertyValue("--data-background-color");
    });
</script>

<div class="container">
    {#if flag}
        <button
            on:click={() => {
                flag = false;
            }}
            ><img
                src={x}
                alt="close menu"
                title="close menu"
                width="32"
                height="32"
            />
        </button>
    {:else}
        <button
            on:click={() => {
                flag = true;
            }}
        >
            <img
                src={bars}
                alt="open menu"
                title="open menu"
                width="32"
                height="32"
            />
        </button>
    {/if}

    {#if flag}
        <div class="data">
            {#if sameColor}
                <div class="divider"></div>
            {/if}
            {#each dropdownList as item, index}
                <div class="item">
                    <a class="item" href={item.link}>
                        <p>{item.text}</p>
                    </a>
                </div>
                {#if index != dropdownList.length - 1}
                    <div class="divider"></div>
                {/if}
            {/each}
        </div>
    {/if}
</div>

<style>
    p{
        font-size: var(--font-size-text);
    }
    .container {
        background-color: var(--image-background-color);
        display: flex;
        justify-content: center;
        align-items: center;
        align-content: center;
        flex-direction: column;
    }
    button {
        background-color: var(--image-background-color);
        border: none;
    }
    .item {
        width: 100%;
        display: flex;
        justify-content: center;
    }
    .item:hover {
        background-color: var(--data-hover-background-color);
    }
    a {
        width: 100%;
        height: 100%;
        text-decoration: none;
        color: black;
    }
    .data {
        width: 100%;
        background-color: var(--data-background-color);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }
    .divider {
        background-color: var(--divider-color);
        height: 3px;
        width: 75%;
    }
</style>
