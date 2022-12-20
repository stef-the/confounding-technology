<script>
	import { each } from 'svelte/internal';

	const space = ' ';
	const definitions = [
		[
			'Adjective',
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
			'Verb',
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
</script>

<div class="bg-gradient-to-b from-gray-900 to-zinc-900 h-screen grid place-content-center">
	<b>
		<h1 class="text-4xl underline-offset-2 p-8">
			Welcome to
			<p class="underline decoration-sky-500">Confounding Technologies</p>
		</h1>
	</b>
</div>
<div class="content">
	<section class="p-8">
		{#each definitions as definition}
			<div class="flex flex-row">
				<div class="bg-gray-100 w-2 h-24 mt-4" />
				<div class="pl-4">
					<br /><b
						><h3 class="leading-4 text-2xl pb-4 underline decoration-sky-500">
							{definition[0]}
						</h3></b
					>
					<ul class="pl-4">
						{#each definition.slice(1) as cat}
							<li>{cat[0]}<br />
                                <div class="pl-6"><i>{cat[1]}</i><br /><br /></div>
                            </li>
						{/each}
					</ul>
				</div>
			</div>
		{/each}
	</section>
	<section class="p-8">
		<div class="flex flex-row">
			<div class="bg-gray-100 w-2 h-24 mt-4" />
			<div class="pl-4">
				<h3 class="leading-4 text-2xl pb-4 underline decoration-pink-500">
					Hello! My name is Stefan, and I like to program.
				</h3>
			</div>
		</div>
	</section>
</div>
