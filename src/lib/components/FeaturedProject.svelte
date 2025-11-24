<script module>
	/** @typedef {Object} Props
	 * @property {'left' | 'right'} [position]
	 * @property {import('./Project.svelte').Project} project
	 */
</script>

<script>
	import { SquareArrowOutUpRight } from '@lucide/svelte';

	import github from '$lib/assets/github.svg';

	/** @type Props */
	let { position = 'right', project } = $props();

	/** @type function(...string): string */
	function clsx(...classNames) {
		return classNames.join(' ');
	}
</script>

<div class="mb-20 grid grid-cols-12">
	<div
		class={clsx(
			'flex items-center',
			position === 'right'
				? 'col-start-1 col-end-7 row-start-1 row-end-1'
				: 'col-start-7 -col-end-1 row-start-1 row-end-1'
		)}
	>
		<div class="relative z-10 grid gap-2" class:text-end={position === 'left'}>
			<div>
				<p class="text-sm text-slate-500">Featured Project</p>
				<h3 class="text-xl">{project.name}</h3>
			</div>
			<div class="grid gap-4 bg-slate-800 p-4 text-white">
				{#if project.description instanceof Array}
					{#each project.description as text}
						<p>{text}</p>
					{/each}
				{:else}
					<p>{project.description}</p>
				{/if}
			</div>
			<ul class="flex gap-4 font-mono text-sm" class:justify-end={position === 'left'}>
				{#each project.stack as technology}
					<li>{technology}</li>
				{/each}
			</ul>
			<div class="flex gap-2" class:justify-end={position === 'left'}>
				{#if project.githubLink}
					<a href={project.githubLink}><img class="h-5 w-5" src={github} alt="GitHub" /></a>
				{/if}
				{#if project.link}
					<a href={project.link}><SquareArrowOutUpRight class="h-5 w-5" /></a>
				{/if}
			</div>
		</div>
	</div>
	<div
		class={clsx(
			'min-h-96 bg-slate-900 transition-colors duration-500 hover:bg-slate-700',
			position === 'right'
				? 'col-start-6 -col-end-1 row-start-1 -row-end-1'
				: 'col-start-1 col-end-8 row-start-1 row-end-1'
		)}
	></div>
</div>
