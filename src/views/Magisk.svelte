<script>
	import { onMount } from 'svelte';
	
	import Spinner from './../components/Spinner.svelte';
	
	let data = [];
	
	onMount(async () => {
		const res = await fetch('./data/version.json');
		const _data = await res.json();
		data = _data;
	});
</script>

<style>
	.card-image {
		height: 200px;
	}
</style>

<div class="container">
	<div class="row">
		<h3 class="center-align">Magisk Versions</h3>
		{#each data as content (content.id)}
			{#if content.support.magisk}
				<div class="col s12 m6 l4">
					<div class="card">
						<div class="card-image waves-effect waves-block waves-light">
							<img class="activator" src="kitana.jpeg" alt="Kitana Tweak">
							<span class="card-title activator white-text">{ content.title }</span>
						</div>
						<div class="card-content">
							<i class="material-icons activator right">more_vert</i>
							<a style="color: #333;" href="downloads/{ content.file_path }"><i class="material-icons left">file_download</i></a>
						</div>
						<div class="card-reveal">
							<span class="card-title grey-text text-darken-4">What's New<i class="material-icons right">close</i></span>
							<ol>
								{#each content.versionInfo as info}
									<li>{ info }</li>
								{/each}
							</ol>
						</div>
					</div>
				</div>
			{/if}
		{:else}
			<Spinner/>
		{/each}
	</div>
</div>