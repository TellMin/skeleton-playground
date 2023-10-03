<script lang="ts">
	import { filter } from '@skeletonlabs/skeleton';
	import Indigo from '$lib/assets/indigo.svelte';

	const filters = [
		'None',
		'Apollo',
		'BlueNight',
		'Emerald',
		'GreenFall',
		'Noir',
		'NoirLight',
		'Rustic',
		'Summer84',
		'XPro'
	];

	let currentFilter = filters[0];
</script>

<div class="border m-8 rounded-xl border-cyan-700 flex justify-center items-center h-[40vh]">
	<div
		class="w-[70vw] max-h-full flex justify-center items-center"
		use:filter={`#${currentFilter}`}
	>
		<Indigo />
	</div>
	<p class="font-mono text-sm text-gray-500">
		{currentFilter}
	</p>
</div>

<div class="card p-4 grid grid-cols-[auto_1fr_auto] gap-4 items-center m-8 variant-ringed-surface">
	<!-- Full Images -->
	<div class="snap-x snap-mandatory scroll-smooth flex overflow-x-auto">
		{#each filters as skeletonFilter}
			<div use:filter={`#${skeletonFilter}`} class="text-center">
				<button
					class="w-12vw h-full text-sm mx-2"
					on:click={() => (currentFilter = skeletonFilter)}
				>
					<Indigo />
					{skeletonFilter}
				</button>
			</div>
		{/each}
	</div>
</div>

<style>
	.w-12vw {
		width: 12vw;
	}
</style>
