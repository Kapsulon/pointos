<script lang="ts" context="module">
    export async function getJsonstudent(): Promise<any> {
        const file = await fetch("src/students.json").then((res) => res.text());
        return JSON.parse(file);
    }
</script>
