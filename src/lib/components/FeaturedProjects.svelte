<script>
	import FeaturedProject from './FeaturedProject.svelte';

	/** @type import('./FeaturedProject.svelte').Project[] */
	const projects = [];
</script>

{#each projects as project, i}
	<FeaturedProject position={i % 2 === 0 ? 'left' : 'right'} {project} />
{/each}
