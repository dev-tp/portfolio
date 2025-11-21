<script module>
	/** @typedef {Object} Props
	 * @property {any} children
	 * @property {string} [href]
	 * @property {(event: MouseEvent) => void} [onclick]
	 */
</script>

<script>
	/** @type Props */
	let { children, href, onclick } = $props();

	const className =
		'inline-block border bg-white px-4 py-2 transition-transform ease-in-out hover:-translate-1';
</script>

<div class="bg-black">
	{#if href}
		<a class={className} {href} target="_blank">
			{@render children()}
		</a>
	{:else}
		<button class={className} {onclick}>
			{@render children()}
		</button>
	{/if}
</div>
