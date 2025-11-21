<script module>
	/** @typedef {Object} Section
	 * @property {string} id
	 * @property {string} name
	 */

	/** @typedef {Object} Props
	 * @property {Section[]} sections
	 */
</script>

<script>
	import Button from './Button.svelte';

	/** @type Props */
	let { sections } = $props();

	let hide = $state(false);
	let offset = $state(0);
</script>

<svelte:window
	onscroll={(event) => {
		hide = event.currentTarget.pageYOffset > offset;
		offset = event.currentTarget.pageYOffset;
	}}
/>

<nav
	class="fixed top-0 right-0 left-0 z-20 flex h-20 items-center justify-end bg-white px-12"
	class:hidden={hide}
	class:shadow={offset > 0}
>
	<ul class="flex gap-4">
		{#each sections as section}
			<li class="px-4 py-2">
				<a href={`#${section.id}`}>{section.name}</a>
			</li>
		{/each}
		<li><Button href="#">Résumé</Button></li>
	</ul>
</nav>
