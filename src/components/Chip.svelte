<style>
	.center {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 20px;
	}
	
	
</style>

<script>
	import { onMount } from 'svelte';
	
	let data = [];
	
	onMount(async () => {
		const res = await fetch('./data/tags.json');
		const _data = await res.json();
		data = _data;
	});
</script>

<div class="center">
	<div class="row">
		<h2>Why Kitana Tweak?</h2>
		{#each data as content (content.id)}
			<div class="col s12 m6">
				<div class="chip waves-effect waves-light" style="width: 300px; height: 40px;">
					<div style="margin: 4px; text-align: left;">
						<i class="left close material-icons">{ content.icon }</i>
						{ content.title }
					</div>
				</div>
			</div>
		{/each}
	</div>
</div>