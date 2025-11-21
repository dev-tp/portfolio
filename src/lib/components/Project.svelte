<script module>
	/** @typedef {Object} Project
	 * @property {string} name
	 * @property {string | string[]} description
	 * @property {string[]} stack
	 * @property {string} [githubLink]
	 * @property {string} [link]
	 */

	/** @typedef {Object} Props
	 * @property {Project} project
	 */
</script>

<script>
	import { Folder, SquareArrowOutUpRight } from '@lucide/svelte';

	import github from '$lib/assets/github.svg';

	/** @type Props */
	let { project } = $props();
</script>

<div class="flex flex-col border p-8 shadow-md transition-transform hover:-translate-y-2">
	<div class="flex grow flex-col gap-2">
		<div class="flex items-center justify-between">
			<Folder class="h-10 w-10" />
			<div class="flex gap-4">
				{#if project.githubLink}
					<a href={project.githubLink}><img class="h-5 w-5" src={github} alt="GitHub" /></a>
				{/if}
				{#if project.link}
					<a href={project.link}><SquareArrowOutUpRight class="h-5 w-5" /></a>
				{/if}
			</div>
		</div>
		<h4 class="text-lg">{project.name}</h4>
		<p>{project.description}</p>
	</div>
	<ul class="mt-4 flex gap-4 font-mono text-sm">
		{#each project.stack as item}
			<li>{item}</li>
		{/each}
	</ul>
</div>
