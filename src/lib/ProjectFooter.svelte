<script>
    import { onMount } from "svelte";
    export let projectFooter;
    export let text_color = "#000000";
    export let background_color = "#5b7553";
    export let left_side = "Martín Ernesto Coronel";
    export let center_test = "Derechos reservados etc etc etc";
    onMount(() => {
        document.documentElement.style.setProperty("--text-color", text_color);
        document.documentElement.style.setProperty(
            "--background-color",
            background_color,
        );
    });
</script>

<div class="container">
    <p class="left">{left_side}</p>
    <p>{center_test}</p>
    <div class="images">
        <a href={projectFooter[2].link}
            ><img
                src={projectFooter[2].icon}
                width="28"
                height="28"
                alt={projectFooter[2].desc}
            /></a
        >
        <a href={projectFooter[0].link}>
            <img
                src={projectFooter[0].icon}
                width="28"
                height="28"
                alt={projectFooter[0].desc}
            />
        </a>
        <a href={projectFooter[1].link}>
            <img
                src={projectFooter[1].icon}
                width="28"
                height="28"
                alt={projectFooter[1].desc}
            />
        </a>
    </div>
</div>

<style>
    p {
        color: var(--text-color);
    }
    .container {
        width: 100%;
        display: flex;
        flex-direction: row;
        background-color: var(--background-color);
        height: 100%;
        justify-content: space-between;
    }
    .images {
        width: 30%;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: center;
    }
    .left {
        padding-left: 15px;
    }
</style>
