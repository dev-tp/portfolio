<script>
	import FeaturedProject from './FeaturedProject.svelte';

	/** @type import('./Project.svelte').Project[] */
	const projects = [];
</script>

{#if projects.length === 0}
	<h3 class="p-4 text-center text-xl">No featured projects at the moment</h3>
{:else}
	<div class="mb-8 grid gap-8 md:gap-20">
		{#each projects as project, i}
			<FeaturedProject position={i % 2 === 0 ? 'left' : 'right'} {project} />
		{/each}
	</div>
{/if}
