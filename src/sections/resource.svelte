<script lang="ts">
	import Modal from '../components/modal/modal.svelte';
	export let showModal: boolean = false;
</script>

<div>
	<Modal bind:showModal>
		{#snippet header()}
			<h2 class="text-xl font-medium text-black">Title of the modal</h2>
		{/snippet}
		<p class="pt-4">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Reiciendis natus, voluptas eveniet
			dolores blanditiis voluptatibus a ullam similique accusamus corrupti alias eligendi, est aut
			vitae consequuntur? Saepe nobis nesciunt mollitia!
		</p>
	</Modal>
	Table inside
</div>
