<script lang="ts" context="module">
    import { getJsonstudent } from "$lib/jsonparser.svelte";
    import { get } from "svelte/store";

    function getTotalTime(time_entries: any): number {
        let now = Date.now();
        let total = 0;

        for (let i = 0; i < time_entries.length; i++) {
            if (time_entries[i].type == "in") {
                if (i + 1 < time_entries.length && time_entries[i + 1].type == "out") {
                    total += Number(time_entries[i + 1].date) - Number(time_entries[i].date);
                } else {
                    total += now - Number(time_entries[i].date);
                }
            }
        }
        return total;
    }

    export async function createCards():Promise<void> {
        let data: any = await getJsonstudent()
        let students = document.createElement("div");
        students.classList.add("students");
        for (let key in data) {
            let student = students.appendChild(document.createElement("div"));
            student.classList.add("student");
            let emoji = student.appendChild(document.createElement("span"));
            if (getTotalTime(data[key].time_entries) > 21600 * 1000) {
                emoji.innerHTML = "🔥";
                emoji.classList.add("finished");
            } else if (!data[key].out) {
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
