<script lang="ts">
	let { name, version, description, website } = $props();
</script>

<p>
	The <code class=" bg-amber-500 px-5 py-2 rounded-2xl">{name}</code> package is {description}. Download version {version} from
	<a href="https://www.npmjs.com/package/{name}">npm</a>
	and <a class=" underline" href={String(website)}>learn more here</a>
</p>
