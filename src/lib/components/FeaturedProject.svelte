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

<div class="grid grid-cols-12 text-white md:text-black">
	<div
		class={clsx(
			'col-start-1 -col-end-1 row-start-1 row-end-1 flex items-start md:items-center',
			position === 'right' ? 'md:col-end-7' : 'md:col-start-7'
		)}
	>
		<div class="relative z-10 grid gap-4 p-8 md:p-0" class:md:text-end={position === 'left'}>
			<div>
				<p class="text-sm text-slate-500">Featured Project</p>
				<h3 class="text-xl">{project.name}</h3>
			</div>
			<div class="grid gap-4 text-white md:bg-slate-800 md:p-4">
				{#if project.description instanceof Array}
					{#each project.description as text}
						<p>{text}</p>
					{/each}
				{:else}
					<p>{project.description}</p>
				{/if}
			</div>
			<ul
				class="flex gap-4 overflow-auto font-mono text-sm text-nowrap"
				class:md:justify-end={position === 'left'}
			>
				{#each project.stack as technology}
					<li>{technology}</li>
				{/each}
			</ul>
			<div class="flex gap-4" class:md:justify-end={position === 'left'}>
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
			'col-start-1 -col-end-1 row-start-1 bg-slate-900 transition-colors duration-500 hover:bg-slate-700 md:min-h-96',
			position === 'right' ? '-row-end-1 md:col-start-6' : 'row-end-1 md:col-end-8'
		)}
	></div>
</div>
