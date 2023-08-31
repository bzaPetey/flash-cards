<script lang="ts">
	type answer = {
		isCorrect: boolean;
		text: string;
	};
	export let data: answer;
	export let selected = false;
</script>

<button
	class={`px-8 py-4 w-full border-2 rounded duration-150  ${
		selected ? 'bg-blue-300 border-blue-500' : 'bg-slate-300 border-slate-500'
	}` + ' hover:scale-110'}
	on:click={() => {
		selected = !selected;
	}}
>
	{data.text}
</button>
