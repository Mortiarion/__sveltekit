<script lang="ts">
	import '../app.css';
	let { children } = $props();
</script>

<div class="flex flex-col">
	<section>
		<nav class="flex gap-5 items-center py-2 px-4 justify-between">
			<a href="/">Logo</a>
			<ul class="flex gap-5">
				<li><a href="/">Art galery</a></li>
				<li><a href="/">Blog post</a></li>
				<li><a href="/">Components</a></li>
				<li><a href="/tutorial">Tutorial</a></li>
			</ul>
			<div>
				<button type="button">User</button>

			</div>
		</nav>
	</section>

	<main class="flex-auto min-h-screen">
		{@render children()}
	</main>

	<section>
		<h1>FOOTER</h1>
	</section>
</div>

<style lang="postcss">
	section {
		border: 2px solid;

		a {
			border: 2px solid skyblue;
		}

		button {
			border: 2px solid firebrick;
		}
	}
</style>