<script>
    import Tables from "../lib/Tables.svelte";
    import { list, dropdownList, projectFooter } from "$lib/props.js";
    import Dropdown from "$lib/Dropdown.svelte";
    import ProjectFooter from "$lib/ProjectFooter.svelte";
</script>

<!-- <div style="width:50%;">
    <Tables
        {list}
        header_background_color="#5B7553"
        header_color="#000000"
        data_background_color="#C6ECAE"
        border="1px solid #646F58"
        data_color="#000000"
    />
</div> -->

<!-- <div style="width:40%; height:400px;">
    <Dropdown
        {dropdownList}
        image_background_color="#5B7553"
        data_background_color="#5B7553"
        data_hover_background_color="#4b8a72"
    />
</div> -->

<div style="width:100%; height:20%;">
    <ProjectFooter text_color="#000000" {projectFooter} />
</div>
