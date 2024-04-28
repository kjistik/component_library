<script>
    import { onMount } from "svelte";

    export let list;
    let keys = Object.keys(list[0]);
    export let header_background_color = "#F5F5F5";
    export let data_background_color = "FFFFFF";
    export let border = "1px solid #ddd";
    export let header_color = "white";
    export let data_color = "black";

    onMount(() => {
    let style = document.documentElement.style
        style.setProperty(
            "--header-background",
            header_background_color,
        );
        style.setProperty(
            "--header-color",
            header_color,
        );
        style.setProperty("--header-border", border);
        style.setProperty(
            "--data-background-color",
            data_background_color,
        );
        style.setProperty("--data-border", border);
        style.setProperty("--data-color", data_color);
    });
</script>

<div>
    <table>
        <tr>
            {#each keys as key}
                {#if key != "id"}
                    <th>{key}</th>
                {/if}
            {/each}
        </tr>
        {#each list as item}
            <tr>
                {#each Object.entries(item) as property}
                    {#if property[0] != "id"}
                        {#if property[0] != "unit"}<td>{property[1]}</td>
                        {:else}
                            <td>{property[1].name}</td>
                        {/if}
                    {/if}
                {/each}
            </tr>
        {/each}
    </table>
</div>

<style>
    :root {
        --header-color: "white";
        --header-background: "darkslategray";
        --header-border: "1px solid black";
        --data-color: "white";
        --data-background-color: "gray";
        --data-border: "1px solid black";
    }
    table {
        border-collapse: collapse;
        width: 100%;
        margin: 0 auto; /* Centers the table horizontally */
    }
    th,
    td {
        text-align: left;
        padding: 10px 15px; /* Adjust padding for desired spacing */
    }
    th {
        border: var(--header-border);
        font-weight: bold;
        background-color: var(--header-background);
        color: var(--header-color);
    }
    td {
        background-color: var(--data-background-color);
        color: var(--data-color);
        border: var(--data-border)
    }
</style>
