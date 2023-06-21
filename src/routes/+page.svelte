<script lang="ts">
    import { onMount } from "svelte";
    import { createCards } from "$lib/studentcard.svelte";
    import twemoji from "twemoji";
    onMount(() => {
        function delay(ms: number) {
            return new Promise( resolve => setTimeout(resolve, ms) );
        }

        async function scrollLoop() {
            while (true) {
                await delay(20);
                window.scrollBy(0,1);
                if (window.scrollY >= document.body.scrollHeight - window.innerHeight) {
                    window.scrollTo(0,0);
                    // delete div with class students
                    let students = document.querySelector(".students");
                    if (students)
                        students.remove();
                    createCards().then(() => {
                        twemoji.parse(document.body);
                    });
                }
            }
        }

        createCards().then(() => {
            twemoji.parse(document.body);
            scrollLoop();
        });
    });
</script>

<html lang="en">
    <head>
        <title>Pointos</title>
        <link rel="stylesheet" href="src/style/main.scss">
    </head>
</html>
