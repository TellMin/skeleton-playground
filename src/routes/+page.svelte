<script lang="ts">
	import { filter } from '@skeletonlabs/skeleton';
	import Indigo from '$lib/assets/indigo.svelte';

	let elemCarousel: HTMLDivElement;
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
	function carouselLeft(): void {
		const x =
			elemCarousel.scrollLeft === 0
				? elemCarousel.clientWidth * elemCarousel.childElementCount // loop
				: elemCarousel.scrollLeft - elemCarousel.clientWidth; // step left
		elemCarousel.scroll(x, 0);
	}
	function carouselRight(): void {
		const x =
			elemCarousel.scrollLeft === elemCarousel.scrollWidth - elemCarousel.clientWidth
				? 0 // loop
				: elemCarousel.scrollLeft + elemCarousel.clientWidth; // step right
		elemCarousel.scroll(x, 0);
	}
</script>

<div class="card p-4 grid grid-cols-[auto_1fr_auto] gap-4 items-center m-8 variant-ringed-surface">
	<!-- Button: Left -->
	<button type="button" class="btn-icon variant-filled" on:click={carouselLeft}>
		<i class="fa-solid fa-arrow-left" />
	</button>
	<!-- Full Images -->
	<div bind:this={elemCarousel} class="snap-x snap-mandatory scroll-smooth flex overflow-x-auto">
		{#each filters as skeletonFilter}
			<div use:filter={`#${skeletonFilter}`} class="min-w-[70%] text-center">
				<Indigo />
				{skeletonFilter}
			</div>
		{/each}
	</div>
	<!-- Button: Right -->
	<button type="button" class="btn-icon variant-filled" on:click={carouselRight}>
		<i class="fa-solid fa-arrow-right" />
	</button>
</div>
