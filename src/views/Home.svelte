<script>
	import { onMount } from 'svelte';
	
	import Chip from './../components/Chip.svelte';
	import Spinner from './../components/Spinner.svelte';
	
	let data = [];
	
	onMount(async () => {
		const res = await fetch('./data/information.json');
		const _data = await res.json();
		data = _data;
	});
</script>

<style>
	.background-image {
		display: flex;
		justify-content: center;
		align-items: center;
		color: #fff;
		width: 100%;
		height: 37.5rem;
		background: url('kitana.jpeg') top/cover #000000;
	}
	
	@media only screen and (max-width: 768px) {
		.background-image {
			height: 25rem;
		}
	}
	
	.background-image__text h1 {
		padding: 0; margin: 0;
	}
	
	.background-image__text p {
		text-align: right;
	}
	
	.card {
		height: 210px;
	}
</style>

<div class="background-image waves-effect waves-light">
	<div class="background-image__text">
		<h1>Kitana Tweak</h1>
		<p>- power of your android!</p>
	</div>
</div>

<Chip/>

<hr />

<div class="container">
	<div class="row">
		{#each data as content (content.id)}
			<div class="col s12 m6">
				<div class="card blue-grey darken-1 waves-effect waves-light">
					<div class="card-content white-text">
						<span class="card-title">{ content.title }</span>
						<p>{ @html content.description }</p>
					</div>
				</div>
			</div>
		{:else}
			<Spinner/>
		{/each}
	</div>
</div>
