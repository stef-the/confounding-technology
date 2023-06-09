<script>
	import { error } from '@sveltejs/kit';
	import { each, text } from 'svelte/internal';
	import Time from 'svelte-time';

	let current = '';
	let currentHover = '';
	const space = ' ';

	const colours = ['sky-500', 'pink-500', 'indigo-500'];

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
			title: 'Ice Core Data Charts',
			description:
				'Visualising and interacting with CO₂ trends from before the year 0 using ice core data.',
			url: 'http://stefff.me/co2-icecore-visualisation/',
			image: 'icecore.png',
			github: 'stef-the/co2-icecore-visualisation'
		},
		{
			title: 'Vine (Service)',
			description:
				'A school project that scrapes Wikipedia and then reformats it to be more interesting to read.',
			url: 'https://vine.stefff.me/',
			image: 'vine.png',
			github: 'stef-the/vine-school'
		},
		{
			title: 'Ascella.host',
			description:
				'A marketing website built for an incredibly quick image uploader that utilizes Rust.',
			url: 'https://Ascella.host/',
			image: 'ascella.png',
			github: 'ascellahost/web'
		},
		{
			title: 'CIT Generator v3',
			description:
				'A 1.8.9 Optifine CIT generation tool designed to automate Hypixel Skyblock texture pack creation.',
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
			title: 'Fulham Library Coding Club',
			description:
				'Teaching basic computer scicence skills to children aged 7-14 using Blocky, Scratch, Python and Minecraft.',
			url: 'https://bit.ly/code-camp-fulham',
			image: 'codeclub.png',
			github: false
		}
	];

	/**
	 * @param {{ org: any; repo: any; }} params
	 */
	async function load(params) {
		const res = await fetch(
			`https://github-latest-commit.stefff.workers.dev/?org=${params.org}&repo=${params.repo}`
		);
		const data = await res.text();
		return data;
	}
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
		<h1 class="text-4xl p-8">
			<p class="pl-3 pb-2">Welcome to</p>
			<p
				class="bg-gradient-to-br from-sky-500 to-pink-500 via-purple-500 rounded p-3 pt-1 gradient-xy"
			>
				Confounding Technologies
			</p>
		</h1>
	</b>
	<a href="#page" class="absolute top-[85%] left-1/2 h-20 w-20 animate-arrow-onload"
		><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"
			><path
				d="M16.924 9.617A1 1 0 0 0 16 9H8a1 1 0 0 0-.707 1.707l4 4a1 1 0 0 0 1.414 0l4-4a1 1 0 0 0 .217-1.09z"
				style="fill:#F3F4F6"
				data-name="Down"
			/></svg
		></a
	>
</div>
<div class="content" id="page">
	<section class="p-8">
		<div class="flex flex-row">
			<h2 class="text-3xl pb-4">
				Hello! My name is <b
					class="bg-gradient-to-br from-purple-500 to-pink-500 via-pink-500 rounded py-0.5 px-1 gradient-xy"
					>Stefan</b
				> and I am a full-stack developer.
			</h2>
		</div>
	</section>
	<section class="p-8 pt-0">
		<h2 class="text-3xl cursor-default">
			I solve confounding problems. What does <b
				class="bg-gradient-to-br from-purple-500 to-indigo-500 
					rounded 
					py-0.5 px-1 gradient-xy">Confounding</b
			>
			mean? <!-- Gradient border WIP: "before:content-none before:absolute before:top-0 before:left-0 before:right-0 before:bottom-0 before:z-0"-->
		</h2>
		{#each definitions as definition}
			<div class="flex flex-row">
				<div
					class="transition-all rounded p-4 pb-3 m-3 mt-2 mb-0
					border-2 border-transparent hover:border-sky-500
                        {current === `dropdown-${definition[0][1]}`
						? 'bg-gradient-to-r from-indigo-500 from-25% to-sky-500 to-100% rounded p-3'
						: ''}
						{currentHover === `dropdown-${definition[0][1]}` ? '' : ''}"
					on:click={() => {
						if (current === '') {
							current = `dropdown-${definition[0][1]}`;
						} else {
							current = '';
						}
					}}
					on:mouseenter={() => (currentHover = `dropdown-${definition[0][1]}`)}
					on:mouseleave={() => (currentHover = ``)}
				>
					<button class="dropdown-button" type="button" id="dropdownMenuButton">
						<h3 class="leading-4 text-2xl">
							{definition[0][0]}{space}<b class="underline decoration-sky-500">{definition[0][1]}</b
							>
						</h3>
					</button>
					<ul
						id="dropdown-{definition[0][1]}"
						class="pl-4 dropdown-menu {current === `dropdown-${definition[0][1]}` ? '' : 'hidden'}"
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
	<section class="p-8 pt-0">
		<!-- 
		
			Portfolio elements: Lots of little websites
		
		-->
		<h2 class="text-3xl cursor-default">
			Here are some of my <b
				class="bg-gradient-to-br from-sky-500 to-indigo-500 rounded py-0.5 px-1 gradient-xy"
				>Projects</b
			>:
		</h2>
		<div class="flex flex-wrap">
			{#each portfolioitems as item}
				<div
					class="transition-all sm:w-100 md:w-[45%] lg:w-[29%] h-100 bg-zinc-800 rounded-xl mt-8 mr-8 p-5 flex flex-col border-2 border-transparent hover:border-gray-100"
				>
					<img class="mb-3 rounded" src="img/{item.image}" alt={item.image} />
					<h3
						class="sm:text-2xl underline decoration-{colours[
							Math.floor(Math.random() * colours.length)
						]}"
					>
						<a href={item.url} target="_blank" rel="noreferrer"><b>{item.title}</b></a>
					</h3>
					<span class="cursor-default">{item.description}</span>
					{@html item.github == false
						? ''
						: `<span class="text-gray-500">
						<a
							class="underline"
							href="https://github.com/${item.github}"
							target="_blank"
							rel="noreferrer"
						>
							${item.github}
						</a>
						<!--{#await load({ org: item.github.split('/')[0], repo: item.github.split('/')[1] })}
							• loading...
						{:then res}
							{#if res != 'None'}
								• <Time relative timestamp={res} />
							{/if}
						{/await}-->
					</span>`}
				</div>
			{/each}
		</div>
	</section>
</div>
