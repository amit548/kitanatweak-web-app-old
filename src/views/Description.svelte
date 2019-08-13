<script>
	import { onMount, afterUpdate } from 'svelte';
	import { Link } from 'svelte-routing';
	
	import Spinner from './../components/Spinner.svelte';
	
	afterUpdate( async () => {
		let collapsibles = await document.querySelectorAll('.collapsible')
		for (let i = 0; i < collapsibles.length; i++){
			await M.Collapsible.init(collapsibles[i]);
		}
	});
	
	let data = [];
	
	onMount(async () => {
		const res = await fetch('./data/description.json');
		const _data = await res.json();
		data = _data;
	});
</script>

<style>
	.center {
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>

<div class="container">
	<div class="row">
		<div class="center">
			<h3>Available Tweak Description</h3>
		</div>
		{#each data as content (content.id)}
			<div class="col s12 m6">
				<ul class="collapsible">
					<li>
						<div class="collapsible-header"><i class="material-icons">info</i>{ content.title }</div>
						<div class="collapsible-body"><span>{ content.description }</span></div>
					</li>
				</ul>
			</div>
		{:else}
			<Spinner/>
		{/each}
	</div>
</div>