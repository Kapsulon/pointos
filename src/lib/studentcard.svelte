<script lang="ts" context="module">
    import { getJsonstudent } from "$lib/jsonparser.svelte";
    export function createCards():any {
        getJsonstudent().then((data) => {
            let students = document.createElement("div");
            students.classList.add("students");
            for (let key in data) {
                console.log(data[key]);
            }
        });
    }
</script>