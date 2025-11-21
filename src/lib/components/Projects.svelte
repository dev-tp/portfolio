<script>
	import Button from './Button.svelte';
	import Project from './Project.svelte';

	/** @type import('./Project.svelte').Project[] */
	const projects = [];

	let showMore = $state(false);
</script>

{#if projects.length !== 0}
	<div class="mb-8 text-center">
		<h3 class="text-2xl/10">Other noteworthy projects</h3>
		<a class="font-mono" href="/archive">View the archive</a>
	</div>
	<div class="mb-8 grid grid-cols-3 gap-4">
		{#each projects as project, i}
			{#if i < 6 || showMore}
				<Project {project} />
			{/if}
		{/each}
	</div>
	{#if projects.length > 6}
		<div class="mb-8 flex justify-center">
			<Button onclick={() => (showMore = !showMore)}>
				{showMore ? 'Show Less' : 'Show More'}
			</Button>
		</div>
	{/if}
{/if}
