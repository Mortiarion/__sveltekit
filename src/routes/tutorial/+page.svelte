<script lang="ts">
	import Counter from './Counter.svelte';
	import Nested from './Nested.svelte';
	import PackgeInfo from './PackgeInfo.svelte';

	let nameSvelte = 'Svelte';

	let nameGif = 'Rick Astley';
	let gifSrc = '/image.gif';

	let string: string = `this string contains some <strong>HTML!!!</strong>`;

	let count = $state(0);
	function increment() {
		count += 1;
	}

	let numbers = $state([1, 2, 3, 4, 5, 6, 7, 8]);
	function addNumber() {
		numbers.push(numbers.length + 1);
		console.log($state.snapshot(numbers));
	}

	let total = $derived(numbers.reduce((t, n) => t + n, 0));
	$inspect(numbers).with(console.trace);

	let elapsed = $state(0);
	let interval = $state(1000);

	$effect(() => {
		const id = setInterval(() => {
			elapsed += 1;
		}, interval);

		return () => {
			clearInterval(id);
		};
	});

	const pkg = {
		name: 'svelte',
		version: 5,
		description: 'blazing fast',
		website: 'https://svelte.dev'
	};
</script>

<h1 class=" text-3xl font-bold border-b-2 px-5 mt-5">Tutorial svelte base</h1>

<section class=" container px-10 my-10 flex flex-col gap-3 border-2 mx-auto">
	<div>
		<p class="text-2xl font-medium">Base component svelte (first component)</p>
		<p>Hello {nameSvelte.toUpperCase()}</p>
	</div>
	<div>
		<p class="text-2xl font-medium">Dynamic attributes</p>
		<img src={gifSrc} alt="{nameGif} dances" />
	</div>
	<div>
		<p class="text-2xl font-medium">Styling</p>
		<span>This is span styling</span>
	</div>
	<div>
		<p class="text-2xl font-medium">Nested components</p>
		<Nested answer={'44'} />
	</div>
	<div>
		<p class="text-2xl font-medium">HTML tags</p>
		<p>{@html string}</p>
	</div>
	<div>
		<p class="text-2xl font-medium">State</p>
		<button
			onclick={increment}
			type="button"
			class=" bg-slate-200 py-2 px-5 rounded-2xl hover:bg-slate-400 transition-all"
		>
			Clicked {count}
			{count === 1 ? 'time' : 'times'}
		</button>
	</div>
	<div>
		<p class="text-2xl font-medium">Deep state</p>
		<span>{numbers.join(' + ')} = ...</span>
		<button
			onclick={addNumber}
			type="button"
			class="bg-slate-200 py-2 px-5 rounded-2xl hover:bg-slate-400 transition-all"
		>
			Add number
		</button>
	</div>
	<div>
		<p class="text-2xl font-medium">Derived state</p>
		<span>{numbers.join(' + ')} = {total}</span>
		<button
			class="bg-slate-200 py-2 px-5 rounded-2xl hover:bg-slate-400 transition-all"
			type="button"
			onclick={addNumber}>Add number</button
		>
	</div>
	<div>
		<p class="text-2xl font-medium">Effects</p>
		<span>Elapsed: {elapsed}</span>
		<button
			type="button"
			class="bg-slate-200 py-2 px-5 rounded-2xl hover:bg-slate-400 transition-all"
			onclick={() => (interval /= 2)}
		>
			Speed up
		</button>
		<button
			type="button"
			class="bg-slate-200 py-2 px-5 rounded-2xl hover:bg-slate-400 transition-all"
			onclick={() => (interval *= 2)}
		>
			Slow down
		</button>
	</div>
	<div>
		<p class="text-2xl font-medium">Universal reactivity</p>
		<Counter />
		<Counter />
		<Counter />
	</div>
	<div>
		<p class="text-2xl font-medium">Declaring, default props</p>
		<Nested />
	</div>
	<div>
		<p class="text-2xl font-medium">Spred props</p>
		<PackgeInfo {...pkg} />
	</div>
</section>

<style lang="postcss">
	span {
		color: goldenrod;
		font-family: 'Times New Roman', Times, serif;
		font-size: 1rem;
	}
</style>
