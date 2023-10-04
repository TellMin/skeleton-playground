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

<div>
	<div class="max-w-xl mx-auto mt-8 border-8 border-sky-700 border-dotted">
		<div use:filter={`#${currentFilter}`}>
			<Indigo />
		</div>
		<p class="font-mono text-sm ml-8 text-gray-500">
			{currentFilter}
		</p>
	</div>
</div>

<div class="card p-4 grid grid-cols-[auto_1fr_auto] gap-4 items-center m-8 variant-ringed-surface">
	<!-- Full Images -->
	<div class="snap-x snap-mandatory scroll-smooth flex overflow-x-auto">
		{#each filters as skeletonFilter}
			<div use:filter={`#${skeletonFilter}`} class="text-center">
				<button class="w-12vw text-sm mx-2" on:click={() => (currentFilter = skeletonFilter)}>
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
