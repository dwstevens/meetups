<script>
	import meetups from './meetups-store.js';
	import Button from '../UI/Button.svelte';
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	export let id;

	let selectedMeetup = $meetups.find(i => i.id === id);
</script>

<style>
	section {
		margin-top: 4rem;
	}

	.image {
		width: 100%;
		height: 25rem;
		background: #e7e7e7;
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.content {
		text-align: center;
		width: 80%;
		margin: auto;
	}

	h1 {
		font-size: 2rem;
		font-family: 'Roboto Slab', sans-serif;
		margin: 0.5rem 0;
	}

	h2 {
		font-size: 1.25rem;
		color: #6b6b6b;
	}

	p {
		font-size: 1.5rem;
	}
</style>

<section>
	<div class="image">
		<img src={selectedMeetup.imageUrl} alt={selectedMeetup.title} />
	</div>
	<div class="content">
		<h1>{selectedMeetup.title}</h1>
		<h2>{selectedMeetup.subtitle} - {selectedMeetup.address}</h2>
		<p>{selectedMeetup.description}</p>
		<Button href="mailto:{selectedMeetup.contactEmail}">Contact</Button>
		<Button type="button" mode="outline" on:click={() => dispatch('close')}>
			Close
		</Button>
	</div>
</section>
