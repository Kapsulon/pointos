<script lang="ts" context="module">
    import { getJsonstudent } from "$lib/jsonparser.svelte";
    export async function createCards():Promise<void> {
        let data: any = await getJsonstudent()
        let students = document.createElement("div");
        students.classList.add("students");
        for (let key in data) {
            let student = students.appendChild(document.createElement("div"));
            student.classList.add("student");
            let emoji = student.appendChild(document.createElement("span"));
            if (!data[key].out) {
                emoji.classList.add("spin");
                emoji.innerHTML = "🤙";
            } else {
                emoji.classList.add("out");
                emoji.innerHTML = "👻";
            }
            let info = student.appendChild(document.createElement("ul"));
            info.id = "info";
            let name = info.appendChild(document.createElement("li"));
            name.innerHTML = data[key].login.split("@")[0].replace(".", " ").toUpperCase();
        }
        document.body.appendChild(students);
    }
</script>
