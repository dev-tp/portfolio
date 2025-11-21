<script>
	import Project from './Project.svelte';

	/** @type import('./Project.svelte').Project[] */
	const projects = [];
</script>

{#if projects.length === 0}
	<div class="mb-4 text-center">
		<h3 class="text-xl/10">No other noteworthy projects at the moment</h3>
	</div>
{:else}
	<div class="mb-4 text-center">
		<h3 class="text-xl/10">Other noteworthy projects</h3>
		<a class="font-mono text-sm" href="/archive">View the archive</a>
	</div>
	<div class="grid grid-cols-3 gap-4">
		{#each projects as project}
			<Project {project} />
		{/each}
	</div>
{/if}
