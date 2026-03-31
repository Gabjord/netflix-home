<script>
	import { createEventDispatcher } from 'svelte';

	// @ts-nocheck
	let dispatch = createEventDispatcher();
	let name = '';
	// @ts-ignore
	/**
	 * @type {any}
	 */
	let age;
	let beltColor = '';
	// @ts-ignore
	let skills;
	function handleSubmit() {
		// @ts-ignore
		const person = { name, beltColor, age, skills, id: Math.random() };
		dispatch('addPerson', person);
	}
</script>

<main class="flex h-screen w-screen items-start justify-center">
	<form
		class="flex w-[35%] flex-col items-center justify-center gap-3 rounded bg-white px-6 py-3 pt-7"
		on:submit|preventDefault={handleSubmit}
	>
		<input
			type="text"
			bind:value={name}
			class="w-full rounded border border-gray-500/50 p-2 outline-blue-500"
			placeholder="Enter Your Name"
		/>
		<input
			type="number"
			bind:value={age}
			class="w-full rounded border border-gray-500/50 p-2 outline-blue-500"
			placeholder="Enter Your Age"
		/>
		<!-- checklist -->
		<!-- svelte-ignore a11y_label_has_associated_control -->
		<label class="text-xl font-semibold text-green-500"> which skill do you have ?</label>
		<div class="flex flex-col gap-3 text-lg font-medium text-green-500 lg:flex">
			<input type="checkbox" bind:group={skills} value="fighting" class="" />fighting
			<br />
			<input type="checkbox" bind:group={skills} value="sewing" />sewing <br />
			<input type="checkbox" bind:group={skills} value="swimming" />swimming <br />
		</div>
		<!-- svelte-ignore a11y_label_has_associated_control -->
		<label class="text-xl font-semibold text-green-500"> Select a Belt color ? </label>

		<!-- select options -->
		<select
			bind:value={beltColor}
			class="border border-gray-500/50 p-1 text-lg font-medium text-green-500 outline-blue-500"
		>
			<option value="Red">Red</option>
			<option value=" Blue">Blue</option>
			<option value="Yellow">Yellow</option>
			<option value="Orange">Orange</option>
			<option value="Green">Green</option>
		</select>
		<button
			class="rounded bg-blue-500 px-6 py-3 text-xl font-medium hover:bg-green-500 hover:text-white"
			>submit</button
		>
	</form>
</main>
