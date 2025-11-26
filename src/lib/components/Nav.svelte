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
	import { Menu, X } from '@lucide/svelte';

	import Button from './Button.svelte';

	/** @type Props */
	let { sections } = $props();

	let delta = $state(0);
	let offset = $state(0);
	let open = $state(false);

	function toggleMenu() {
		if (open) {
			document.body.classList.remove('overflow-hidden');
		} else {
			document.body.classList.add('overflow-hidden');
		}

		open = !open;
	}
</script>

<svelte:window
	onscroll={(event) => {
		delta = event.currentTarget.pageYOffset - offset;
		offset = event.currentTarget.pageYOffset;
	}}
/>

{#snippet options()}
	<menu class="flex flex-col items-center gap-4 md:flex-row">
		{#each sections as section}
			<li class="px-4 py-2">
				<a
					href={`#${section.id}`}
					onclick={() => {
						if (open) {
							toggleMenu();
						}
					}}
				>
					{section.name}
				</a>
			</li>
		{/each}
		<li><Button href="#">Résumé</Button></li>
	</menu>
{/snippet}

<nav
	class="fixed top-0 right-0 left-0 z-20 flex h-16 items-center justify-end bg-white px-8 transition-transform duration-500 md:h-20 md:px-12"
	class:-translate-y-20={delta > 0}
	class:shadow={offset !== 0}
>
	<div class="hidden md:block">
		{@render options()}
	</div>
	<div class="block md:hidden">
		<button onclick={() => toggleMenu()}>
			<Menu class="h-6 w-6" />
		</button>
	</div>
</nav>
<div class="fixed inset-0 z-20 bg-black/80 md:hidden" class:hidden={!open}>
	<div class="fixed top-0 right-0 bottom-0 z-30 bg-white">
		<button class="flex w-full justify-center p-4" onclick={() => toggleMenu()}>
			<X class="h-6 w-6" />
		</button>
		{@render options()}
	</div>
</div>
