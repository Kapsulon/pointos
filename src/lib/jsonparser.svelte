<script lang="ts" context="module">
import { readFileSync } from 'fs';
/* fill array json */

export function getJsonstudent(fileName: string): object | null {
    const file = readFileSync(fileName, 'utf-8');
    return JSON.parse(file);
}
</script>