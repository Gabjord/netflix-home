<script>
	import { X } from 'lucide-svelte';
	import AddPerson from './addPerson.svelte';
	export let message = 'welcome';
	export let showModal = false;
	let promo = false;
</script>

<AddPerson />
{#if showModal}
	<!-- svelte-ignore a11y_click_events_have_key_events -->
	<!-- svelte-ignore a11y_no_static_element_interactions -->
	<div class="absolute inset-0 flex items-center justify-center bg-black/80 shadow-2xl">
		<div class=" relative rounded bg-white p-8 text-2xl font-semibold" on:click>
			<p class={promo ? 'text-green-500' : 'text-red-500'}>{message}</p>
			<X class="absolute right-1 top-1 size-8 text-green-400"></X>
		</div>
	</div>
{/if}
