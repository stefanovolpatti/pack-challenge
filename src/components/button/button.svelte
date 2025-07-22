<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher<{ click: MouseEvent }>();
</script>

<button
	on:click={(event) => dispatch('click', event)}
	type="button"
	class="focus:shadow-outline w-full rounded-md bg-orange-500 px-4 py-2 font-bold text-white hover:bg-orange-600 focus:outline-none sm:w-auto"
>
	<slot />
</button>
