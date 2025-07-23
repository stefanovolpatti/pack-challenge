<script lang="ts">
	import { onMount } from 'svelte';
	import Modal from '../components/modal/modal.svelte';
	export let showModal: boolean = false;

	let title = '';
	let description = '';
	let category = '';
	let language = '';
	let type = '';
	let role = '';

	let resources: Array<any> = [];

	onMount(() => {
		const stored = localStorage.getItem('resources');
		if (stored) {
			resources = JSON.parse(stored);
		}
	});

	function resetForm() {
		title = '';
		description = '';
		category = '';
		language = '';
		type = '';
		role = '';
	}

	function saveResource(e: Event) {
		e.preventDefault();
		const newResource = { title, description, category, language, type, role };
		resources = [...resources, newResource];
		localStorage.setItem('resources', JSON.stringify(resources));
		resetForm();
		showModal = false;
	}
</script>

<div>
	<Modal bind:showModal>
		{#snippet header()}
			<h2 class="text-xl font-medium text-black">Upload Resource</h2>
		{/snippet}
		<form class="flex flex-col gap-4 pt-4" on:submit={saveResource}>
			<input
				required
				type="text"
				placeholder="How to deal with conflict in a work environment"
				class="rounded border px-3 py-2"
				bind:value={title}
			/>
			<input
				required
				type="text"
				placeholder="Step by step guide to how to solve conflict caused by miscommunication"
				class="rounded border px-3 py-2"
				bind:value={description}
			/>
			<select class="rounded border px-3 py-2" bind:value={category}>
				<option value="" disabled selected>Category</option>
				<option value="Conflict Resolution">Conflict Resolution</option>
				<option value="Payroll Discussion">Payroll Discussion</option>
			</select>
			<select class="rounded border px-3 py-2" bind:value={language}>
				<option value="" disabled selected>Language</option>
				<option value="English">English</option>
				<option value="Italian">Italian</option>
				<option value="Spanish">Spanish</option>
			</select>
			<select class="rounded border px-3 py-2" bind:value={type}>
				<option value="" disabled selected>Type</option>
				<option value="Pack">Pack</option>
				<option value="Acme">Acme</option>
			</select>
			<select class="rounded border px-3 py-2" bind:value={role}>
				<option value="" disabled selected>Role</option>
				<option value="Mentor / Coach">Mentor / Coach</option>
				<option value="Mentee / Coachee">Mentee / Coachee</option>
			</select>
			<button type="submit" class="self-end rounded bg-orange-500 px-4 py-2 text-white"
				>Upload</button
			>
		</form>
	</Modal>

	{#if resources.length > 0}
		<div class="mt-8 overflow-x-auto rounded-lg bg-white shadow-lg">
			<table class="min-w-full text-sm">
				<thead>
					<tr class="bg-orange-400 text-white">
						<th class="rounded-tl-lg px-4 py-2 text-left font-semibold">Title</th>
						<th class="px-4 py-2 text-left font-semibold">Description</th>
						<th class="px-4 py-2 text-left font-semibold">Category</th>
						<th class="px-4 py-2 text-left font-semibold">Language</th>
						<th class="px-4 py-2 text-left font-semibold">Type</th>
						<th class="rounded-tr-lg px-4 py-2 text-left font-semibold">Role</th>
					</tr>
				</thead>
				<tbody>
					{#each resources as r, i}
						<tr
							class="{i % 2 === 0 ? 'bg-gray-50' : 'bg-white'} transition-colors hover:bg-orange-50"
						>
							<td class="border-b border-gray-200 px-4 py-2">{r.title}</td>
							<td class="border-b border-gray-200 px-4 py-2">{r.description}</td>
							<td class="border-b border-gray-200 px-4 py-2">{r.category}</td>
							<td class="border-b border-gray-200 px-4 py-2">{r.language}</td>
							<td class="border-b border-gray-200 px-4 py-2">{r.type}</td>
							<td class="border-b border-gray-200 px-4 py-2">{r.role}</td>
						</tr>
					{/each}
				</tbody>
			</table>
		</div>
	{/if}
</div>
