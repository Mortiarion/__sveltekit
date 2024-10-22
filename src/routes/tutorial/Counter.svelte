<script lang="ts">
	import { counter } from './shared.svelte';
</script>

<button type="button" onclick={() => (counter.count += 1)} class=" px-5 py-2 bg-red-500 rounded-3xl"
	>Clicks: {counter.count}
</button>
