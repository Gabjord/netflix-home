<script>
	export let fields = { question: '', answerA: '', answerB: '' };
	import { createEventDispatcher } from 'svelte';
	import Button from './button.svelte';
	let dispatch = createEventDispatcher();
	let errors = { question: '', answerA: '', answerB: '' };
	let valid = false;
	const submithandler = () => {
		valid = true;
		if (fields.question.trim().length < 5) {
			valid = false;
			errors.question = 'Question must be at least 5 characters long';
		} else {
			errors.question = '';
		}

		if (fields.answerA.trim().length < 1) {
			valid = false;
			errors.answerA = 'Answer  A Cannot be empty';
		} else {
			errors.answerA = '';
		}

		if (fields.answerB.trim().length < 1) {
			valid = false;
			errors.answerB = 'Answer B cannot be empty';
		} else {
			errors.answerB = '';
		}
		//add new poll
		if (valid) {
			let poll = { ...fields, votesA: 0, votesB: 0, id: Math.random() };
			dispatch('addPoll', poll);
		}
	};
</script>

<form
	class="mx-auto flex w-[400px] flex-col items-center gap-4"
	on:submit|preventDefault={submithandler}
>
	<div class=" w-full">
		<label for="question" class="my-1 block text-[#45c496]">Poll Question:</label>
		<input
			type="text"
			id="question"
			class="w-full cursor-pointer rounded border py-2 outline-blue-500"
			bind:value={fields.question}
		/>
		<div class="mt-2 text-center text-sm font-bold text-red-500">{errors.question}</div>
	</div>
	<div class=" w-full">
		<label for="answer a" class="my-1 block text-[#45c496]">Answer A:</label>
		<input
			type="text"
			id="answer a"
			class="w-full cursor-pointer rounded border py-2 outline-blue-500"
			bind:value={fields.answerA}
		/>
		<div class="mt-2 text-center text-sm font-bold text-red-500">{errors.answerA}</div>
	</div>
	<div class=" w-full">
		<label for="answer b" class="my-1 block text-[#45c496]">Answer B:</label>
		<input
			type="text"
			id="answer b"
			class="w-full rounded border py-2 outline-blue-500"
			bind:value={fields.answerB}
		/>
		<div class="mt-2 text-center text-sm font-bold text-red-500">{errors.answerB}</div>
	</div>
	<Button type="secondary" flat={true}>Add poll</Button>
</form>
