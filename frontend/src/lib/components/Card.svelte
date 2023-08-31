<script lang="ts">
	import Answer from './Answer.svelte';

	let data = {
		question:
			'This is a simulated multiple choice question. Select all of the correct answers. The correct answers are 3 and 5.',
		answers: [
			{ isCorrect: false, text: 'This is answer 1' },
			{ isCorrect: false, text: 'This is answer 2' },
			{ isCorrect: true, text: 'This is answer 3' },
			{ isCorrect: false, text: 'This is answer 4' },
			{ isCorrect: true, text: 'This is answer 5' }
		]
	};

	let selected: boolean[] = [];

	function submit() {
		let points = 0;

		for (let cnt = 0; cnt < data.answers.length; cnt++) {
			if (selected[cnt] === data.answers[cnt].isCorrect) {
				points++;
			}
		}

		console.log(selected, points);
	}
</script>

<div class="border-4 p-12 pt-4 m-4 rounded w-1/2">
	<div class="flex justify-end">
		<div class=" mb-4 text-md font-semibold">1 of 10</div>
	</div>

	<h3 class="mb-8">{data.question}</h3>

	<ol>
		{#each data.answers as answer, index}
			<li class="my-2">
				<Answer data={answer} bind:selected={selected[index]} />
			</li>
		{/each}
	</ol>

	<div class="flex justify-center mt-8">
		<button
			on:click={() => submit()}
			class="px-8 py-4 border-2 border-sky-500 bg-sky-300 rounded hover:scale-110 hover:bg-sky-500 hover:border-sky-700"
			>Submit</button
		>
	</div>
</div>
