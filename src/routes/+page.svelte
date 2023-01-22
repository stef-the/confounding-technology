<script>
	import { error } from '@sveltejs/kit';
	import { each } from 'svelte/internal';

	let current0 = '';
	let currenthover0 = '';

	let whobg = 'bg-zinc-800';

	const space = ' ';

	const pallette = ['sky-500', 'pink-500', 'indigo-500'];

	const definitions = [
		[
			['As an', 'Adjective'],
			[
				'Perplexing or Bewildering',
				"He's hosting an evening of readings from some of the most sensational and confounding cases of Sherlock Holmes."
			],
			[
				'Throwing someone or something into confusion or disorder.',
				'Still in shock, his wife broke the confounding news that their only son had been killed by a stray bullet.'
			],
			[
				'Interacting with both the dependent and independent variables in an experiment or study, making it impossible to determine a causal effect between them.',
				'The authors list potential confounding factors, but it is not clear from the paper whether all of these were controlled for in the analyses.'
			]
		],
		[
			['As a', 'Verb'],
			[
				'The act of perplexing, bewildering, causing confusion or disorder, etc.',
				'The Jaredite civilization is supposed to have formed in the wake of the miraculous confounding of languages at the Tower of Babel.'
			],
			[
				'The act of treating or viewing different things as if they were the same.',
				'I have always found the confounding of Christmas and Hanukkah disturbing.'
			]
		]
	];

	const portfolioitems = [
		{
			title: 'Vine (Service)',
			description: 'A school project that went a little too far.',
			url: 'https://vine.stefff.me/',
			image: 'vine.png',
			github: 'stef-the/vine-school'
		},
		{
			title: 'Ascella.host',
			description: 'An incredibly quick image uploader.',
			url: 'https://Ascella.host/',
			image: 'ascella.png',
			github: 'Tricked-dev/ascella'
		},
		{
			title: 'CIT Generator v3',
			description:
				"The third generation of a 1.8.9 Optifine CIT generation tool for Hypixel Skyblock, using Moulberry's item repository.",
			url: 'https://cit-generator-v3.vercel.app/',
			image: 'citgenv3.png',
			github: 'stef-the/CIT-Generator-v3'
		},
		{
			title: 'Confounding Technologies',
			description: "You're on this site at the moment...",
			url: 'https://confounding.tech/',
			image: 'confoundingtech.png',
			github: 'stef-the/confounding-technology'
		},
		{
			title: 'Ice Core Data Visualiser',
			description: 'Visualising CO2 trends from before the year 0 using ice core data.',
			url: 'http://stefff.me/co2-icecore-visualisation/',
			image: 'icecore.png',
			github: 'stef-the/co2-icecore-visualisation'
		}
	];

	const request = new XMLHttpRequest();

							request.addEventListener("load", function(evt){
								console.log(evt);
							}, false);
							
							request.open('GET', 'a.html', true),
							request.send();
</script>

<svelte:head>
	<title>Confounding Technologies</title>
	<meta name="author" content="stef#6470" />
	<meta
		name="description"
		content="The Confounding Technologies homepage. Confounding is a synonym for Perplexing or Bewildering."
	/>
</svelte:head>

<div class="bg-gradient-to-b from-gray-900 to-zinc-900 h-screen grid place-content-center">
	<b class="cursor-default">
		<h1 class="text-4xl underline-offset-2 p-8">
			Welcome to
			<p class="underline decoration-sky-500">Confounding Technologies</p>
		</h1>
	</b>
</div>
<div class="content">
	<section class="p-8">
		<div class="flex flex-row">
			<div class="{whobg} w-2 h-10 transition-all rounded" id="who" />
			<div
				class="pl-4 cursor-pointer"
				on:mouseenter={() => (whobg = 'bg-gray-100')}
				on:mouseleave={() => (whobg = 'bg-zinc-800')}
			>
				<h3 class="text-2xl pb-4">
					Hello! My name is <b class="underline decoration-pink-500">Stefan</b>, and I like to
					program.
				</h3>
			</div>
		</div>
	</section>
	<section class="p-8">
		<h2 class="text-3xl cursor-default">
			But what does <b class="underline decoration-pink-500">Confounding</b> mean?
		</h2>
		{#each definitions as definition}
			<div class="flex flex-row">
				<div
					class=" h-10 mt-4 w-2 transition-all rounded
                        {current0 === `dropdown-${definition[0][1]}` ? 'bg-sky-500' : ''}
						{currenthover0 === `dropdown-${definition[0][1]}` ? 'bg-gray-100' : 'bg-zinc-800'}"
				/>
				<div class="pl-4">
					<button
						class="dropdown-button"
						type="button"
						id="dropdownMenuButton"
						on:click={() => {
							if (current0 === '') {
								current0 = `dropdown-${definition[0][1]}`;
							} else {
								current0 = '';
							}
						}}
						on:mouseenter={() => (currenthover0 = `dropdown-${definition[0][1]}`)}
						on:mouseleave={() => (currenthover0 = ``)}
						><br />
						<h3 class="leading-4 text-2xl pb-4">
							{definition[0][0]}{space}<b class="underline decoration-sky-500">{definition[0][1]}</b
							>
						</h3>
					</button>
					<ul
						id="dropdown-{definition[0][1]}"
						class="pl-4 dropdown-menu {current0 === `dropdown-${definition[0][1]}` ? '' : 'hidden'}"
					>
						{#each definition.slice(1) as cat}
							<li>
								<b>{cat[0]}</b><br />
								<div class="pl-6"><i>{cat[1]}</i><br /><br /></div>
							</li>
						{/each}
					</ul>
				</div>
			</div>
		{/each}
	</section>
	<section class="p-8">
		<h2 class="text-3xl cursor-default">
			Here's my <b class="underline decoration-indigo-500">Portfolio</b>
		</h2>
		<div class="flex flex-wrap">
			{#each portfolioitems as item}
				<div
					class="transition-all sm:w-100 md:w-[45%] lg:w-[29%] h-100 bg-zinc-800 rounded-xl mt-8 mr-8 p-5 flex flex-col border-2 border-transparent hover:border-gray-100"
				>
					<img class="mb-3 rounded" src="img/{item.image}" alt={item.image} />
					<h3
						class="sm:text-2xl underline decoration-{pallette[
							Math.floor(Math.random() * pallette.length)
						]}"
					>
						<a href={item.url} target="_blank" rel="noreferrer"><b>{item.title}</b></a>
					</h3>
					<span class="cursor-default">{item.description}</span>
					<span class="text-gray-500">
						<a
							class="underline"
							href="https://github.com/{item.github}"
							target="_blank"
							rel="noreferrer"
						>
							{item.github}
						</a>
						• 
					</span>
				</div>
			{/each}
		</div>
	</section>
</div>
