<script lang="ts">
	import Button from '../components/button/button.svelte';
	import Modal from '../components/modal/modal.svelte';
	import Tab from '../components/tab/Tab.svelte';
	import Overview from '../sections/overview.svelte';
	import Resource from '../sections/resource.svelte';
	let activeTab = $state('overview');
	let showModal = $state(false);
</script>

<div>
	<div class="border-b-4 border-gray-300 p-4 shadow-md">Header</div>

	<div class="mx-8 my-8 h-auto rounded-md border-2 border-gray-300 p-8 shadow-md lg:mx-32">
		<div class="mb-4 flex w-full">
			<Tab
				label="Overview"
				active={activeTab === 'overview'}
				on:click={() => (activeTab = 'overview')}
			/>
			<Tab label="All" active={activeTab === 'all'} on:click={() => (activeTab = 'all')} />
		</div>
		{#if activeTab === 'overview'}
			<Overview />
		{:else}
			<div class="sm:ml-0 sm:flex sm:grow-7 sm:justify-end">
				<Button on:click={() => (showModal = true)}>Upload</Button>
			</div>
			<Resource bind:showModal />
		{/if}
	</div>
</div>
