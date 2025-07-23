<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher<{ click: MouseEvent }>();

	export let label: string;
	export let active: boolean = false;
</script>

<button
	class="rounded-t-md border-b-2 px-4 py-2 transition-colors duration-200 focus:outline-none"
	class:border-orange-500={active}
	class:border-transparent={!active}
	class:text-orange-600={active}
	class:text-gray-500={!active}
	on:click={(event) => dispatch('click', event)}
>
	{label}
</button>
