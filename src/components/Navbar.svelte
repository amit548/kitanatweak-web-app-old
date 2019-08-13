<script>
	import { afterUpdate } from 'svelte';
	import { Link } from 'svelte-routing';
	
	afterUpdate( async () => {
		let sidenavs = await document.querySelectorAll('.sidenav');
		for (let i = 0; i < sidenavs.length; i++){
			await M.Sidenav.init(sidenavs[i]);
		}
	});
</script>

<nav>
	<div class="nav-wrapper deep-purple darken-4">
		<a href="javascript:void(0);" data-target="mobile-nav" class="sidenav-trigger show-on-medium-and-down right">
			<i class="material-icons">menu</i>
		</a>
		<Link to="/"><span class="brand-logo left">Kitana Tweak</span></Link>
		<ul class="right hide-on-med-and-down">
			<li>
				<Link to="/">Home</Link>
			</li>
			<li>
				<Link to="/magisk">For Magisk</Link>
			</li>
			<li>
				<Link to="/supersu">For SuperSU</Link>
			</li>
			<li>
				<Link to="/description">Description</Link>
			</li>
			<li>
				<Link to="/about">About</Link>
			</li>
			<li>
				<Link to="/contact">Contact</Link>
			</li>
		</ul>
	</div>
</nav>

<ul class="sidenav" id="mobile-nav">
	<li>
		<Link to="/">Home</Link>
	</li>
	<li>
		<Link to="/magisk">For Magisk</Link>
	</li>
	<li>
		<Link to="/supersu">For SuperSU</Link>
	</li>
	<li>
		<Link to="/description">Description</Link>
	</li>
	<li>
		<Link to="/about">About</Link>
	</li>
	<li>
		<Link to="/contact">Contact</Link>
	</li>
</ul>
