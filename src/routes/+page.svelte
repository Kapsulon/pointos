<script lang="ts">
    import { onMount } from "svelte";
    import { createCards } from "$lib/studentcard.svelte";
    import twemoji from "twemoji";
    onMount(() => {
        createCards().then(() => {
            twemoji.parse(document.body);
        });
    });
</script>

<html lang="en">
    <head>
        <title>Pointos</title>
        <link rel="stylesheet" href="src/style/main.scss">
    </head>
</html>
