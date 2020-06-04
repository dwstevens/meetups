<script>
	import { createEventDispatcher } from 'svelte';
	import TextInput from '../UI/TextInput.svelte';
	import Button from '../UI/Button.svelte';
	import Modal from '../UI/Modal.svelte';

	const dispatch = createEventDispatcher();

	let title = '';
	let subtitle = '';
	let address = '';
	let email = '';
	let description = '';
	let imageUrl = '';
	let isFav;

	function submitForm() {
		dispatch('save-meetup', {
			title: title,
			subtitle: subtitle,
			address: address,
			email: email,
			description: description,
			imageUrl: imageUrl,
		});
	}

	function cancel() {
		dispatch('cancel');
	}
</script>

<style>
	form {
		width: 100%;
	}
</style>

<Modal title="Add New Meetup" on:cancel>
	<form on:submit|preventDefault={submitForm}>
		<TextInput
			id="title"
			label="Title"
			value={title}
			on:input={event => (title = event.target.value)} />
		<TextInput
			id="subtitle"
			label="Subtitle"
			value={subtitle}
			on:input={event => (subtitle = event.target.value)} />
		<TextInput
			id="address"
			label="Address"
			value={address}
			on:input={event => (address = event.target.value)} />
		<TextInput
			id="imageUrl"
			label="ImageUrl"
			value={imageUrl}
			on:input={event => (imageUrl = event.target.value)} />
		<TextInput
			id="email"
			label="E-Mail"
			value={email}
			type="email"
			on:input={event => (email = event.target.value)} />
		<TextInput
			id="description"
			label="Description"
			value={description}
			controlType="textarea"
			on:input={event => (description = event.target.value)} />
	</form>
	<div slot="footer">
		<Button type="button" on:click={submitForm}>Save</Button>
		<Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
	</div>
</Modal>
