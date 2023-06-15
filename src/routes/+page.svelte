<script lang="ts">
    import { onMount } from "svelte";
    import { createCards } from "$lib/studentcard.svelte";
    onMount(() => {
        createCards();
    });
</script>

<html lang="en">
    <head>
        <title>Pointos</title>
        <link rel="stylesheet" href="src/style/main.scss">
        <script src="https://twemoji.maxcdn.com/v/latest/twemoji.min.js" crossorigin="anonymous"></script>
    </head>
    <body>
        <div class="students">
            <div class="student">
                <span class="spin">🤙</span>
                <ul id="info">
                    <li>test2</li>
                    <li>test3</li>
                    <li>test4</li>
                </ul>
            </div>
        </div>
    </body>
    <script>
        twemoji.parse(document.body);
    </script>
</html>
