<script>
	import Button from '$lib/components/Button.svelte';
	import ExperienceTimeline from '$lib/components/ExperienceTimeline.svelte';
	import Nav from '$lib/components/Nav.svelte';

	import github from '$lib/assets/github.svg';

	const about = 'about';
	const contact = 'contact';
	const experience = 'experience';
	const projects = 'projects';

	const sections = [
		{ id: about, name: 'About Me' },
		{ id: experience, name: 'Experience' },
		{ id: projects, name: 'Projects' },
		{ id: contact, name: 'Contact' }
	];
</script>

<Nav {sections} />
<main class="mx-24 font-text">
	<section class="flex h-screen flex-col justify-center">
		<p class="font-mono">Hello, my name is</p>
		<h1 class="font-header text-7xl/21">Erik Sorto</h1>
		<p class="font-header text-6xl/18">I build things for fun.</p>
		<p class="w-full md:w-2/5">
			I'm a software engineer by trade and tinckerer at heart. I dabble in all areas from web design
			to low level, IoT things. When I'm not writing code, you can find me riding my bike around LA
			on the weekends.
		</p>
	</section>
	{#each sections as section}
		<section id={section.id} class="min-h-screen pt-20">
			<h2 class="mb-2 font-header text-2xl">{section.name}</h2>
			{#if section.id === experience}
				<ExperienceTimeline />
			{:else if section.id === contact}
				<div class="flex flex-col items-center gap-4">
					<h3 class="font-header text-2xl">Get in touch</h3>
					<p>
						Whether you have a question or just want to say hi, I’ll try my best to get back to you!
					</p>
					<Button href="mailto:rck.srt@gmail.com">Say Hello</Button>
				</div>
			{/if}
		</section>
	{/each}
</main>
<div class="fixed bottom-0 left-8 flex w-8 flex-col items-center gap-4">
	<a class="sideways-lr" href="https://www.github.com/dev-tp" target="_blank">
		<img class="h-6 w-6" src={github} alt="GitHub" />
	</a>
	<div class="h-24 w-px bg-black"></div>
</div>
<div class="fixed right-8 bottom-0 flex w-8 flex-col items-center gap-4">
	<a class="sideways-lr" href="mailto:rck.srt@gmail.com">rck.srt@gmail.com</a>
	<div class="h-24 w-px bg-black"></div>
</div>
