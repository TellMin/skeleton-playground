<script lang="ts">
	import { filter } from '@skeletonlabs/skeleton';
	import Indigo from '$lib/assets/indigo.svelte';
</script>

<section class="max-w-2xl m-auto mt-8">
	<div
		class="block card card-hover p-2 border-double border-4 border-teal-600"
		style="background-color: transparent;"
	>
		<div use:filter={'#Emerald'}>
			<Indigo />
		</div>
	</div>
</section>
