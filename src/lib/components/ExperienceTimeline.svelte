<script>
	import { fade } from 'svelte/transition';

	const jobs = [
		{
			location: 'Cathedral of Our Lady of the Angels',
			position: 'Web developer & IT',
			tasks: [
				'Build personalized web applications in React to improve office productivity.',
				'Upgrade internal infrastructure and software with open source solutions to eliminate extra costs associated with licenses.',
				'Reverse engineer vital legacy applications written in Java or .NET to sustain some level compatibility when migrating to newer platforms.',
				'Document applications and services with Markdown while keeping track of those changes with Git to avoid paper trails.',
				'Dabble in the maintenance of security systems.'
			],
			tenure: 'January 2018 – August 2025',
			website: 'https://www.olacathedral.org'
		},
		{
			location: 'Countrywide Trial Lawyers',
			position: 'IT (Consulting)',
			tasks: [
				'Deploy and maintain computers using a custom AD server running Linux.',
				'Eliminate the subscription costs for VPN users overseas by deploying a custom WireGuard instance.',
				'Manage internal IP routing for internal and external services including WireGuard and SMB.'
			],
			tenure: 'August 2022 – Present',
			website: 'https://www.countrywidetriallawyers.com'
		},
		{
			location: 'UrbanTxT',
			position: 'Instructor',
			tasks: [
				'Teach a cohort of high school students software engineering with an emphasis on design-driven development.',
				'Lead a group of students to design and implement a mobile app written in Angular with the aim of solving a problem for the music community.',
				'Help students develop interpersonal skills during the internship.'
			],
			tenure: 'May 2016 – August 2016',
			website: 'https://www.urbantxt.org'
		}
	];

	let activeTab = $state(0);
</script>

<div class="flex flex-col gap-4 md:flex-row">
	<div class="overflow-auto md:overflow-clip">
		<ul class="flex overflow-auto md:block">
			{#each jobs as job, tab}
				<li>
					<button
						class="w-full border-b border-slate-900 p-4 text-start font-mono text-sm text-nowrap hover:bg-slate-200 md:border-b-0 md:border-l"
						class:bg-slate-100={tab === activeTab}
						class:border-b-2={tab === activeTab}
						class:border-slate-500={tab === activeTab}
						class:md:border-l-2={tab === activeTab}
						onclick={() => (activeTab = tab)}
					>
						{job.location}
					</button>
				</li>
			{/each}
		</ul>
	</div>
	{#each jobs as job, tab}
		{#if tab === activeTab}
			<div class="grid gap-2 pt-2" in:fade>
				<h3 class="text-xl">
					{job.position}
					<a class="font-bold" href={job.website} target="_blank"> @ {job.location}</a>
				</h3>
				<p>{job.tenure}</p>
				<ul class="list-outside list-disc pl-4">
					{#each job.tasks as task}
						<li class="mb-2">{task}</li>
					{/each}
				</ul>
			</div>
		{/if}
	{/each}
</div>
