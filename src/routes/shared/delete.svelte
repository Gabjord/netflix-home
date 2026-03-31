<script>
	// @ts-ignore
	// svelte-ignore export_let_unused
	/**
	 * @type {any[]}
	 */
	export let users = [];
	import { createEventDispatcher } from 'svelte';
	let dispatch = createEventDispatcher();
	let displayCurrent = false;
</script>

<main>
	{#if users.length > 0}
		<ul class="mt-5">
			{#each users as user (user.id)}
				<li class="flex flex-col items-center justify-center gap-3">
					<div
						class="flex w-full flex-col items-center justify-center gap-5 space-y-4 pb-5 text-center text-base font-medium text-red-500"
					>
						<div class="">
							<p><span class="text-blue-500">username:</span> {user.name}</p>
							<p><span class="text-blue-500">Favourite Color:</span>{user.color}</p>
							<p><span class="text-blue-500">User age:</span> {user.age}</p>
						</div>

						<button
							class=" bg-blue-500 px-6 py-3 text-white"
							on:click={() => dispatch('delete', user.id)}>Delete</button
						>
					</div>
				</li>
			{/each}
		</ul>
	{:else}
		<p class=",text-base mt-5 text-center font-medium text-red-500">NO AVAILABLE USERS</p>
	{/if}
</main>
