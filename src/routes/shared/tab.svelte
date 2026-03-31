<script>
	// @ts-nocheck

	// svelte-ignore export_let_unused
	export let items;
	// svelte-ignore export_let_unused
	export let activeItem;
	import { createEventDispatcher } from 'svelte';
	let dispatch = createEventDispatcher();
	//function handleclick(item) {
	//dispatch('tab', item);
	//	}on:click={handleclick(item)
</script>

<div>
	<ul class="mt-5 flex items-center justify-center gap-3">
		{#each items as item}
			<!-- svelte-ignore a11y_click_events_have_key_events -->
			<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
			<li
				class="mx-4 my-0 text-[17px] text-[#555]"
				on:click={() => {
					dispatch('tabChanger', item);
				}}
			>
				<div
					class={`cursor-pointer pb-3 ${activeItem === item ? 'border-b-2 border-red-600 text-red-600' : 'text-[#555]'}`}
				>
					{item}
				</div>
			</li>
		{/each}
	</ul>
</div>
