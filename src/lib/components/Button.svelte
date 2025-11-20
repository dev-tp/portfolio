<script>
	let { children, href } = $props();
</script>

<div class="bg-black">
	<a
		class="inline-block border bg-white px-4 py-2 transition-transform ease-in-out hover:-translate-1"
		{href}
		target="_blank"
	>
		{@render children()}
	</a>
</div>
