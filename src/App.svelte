<script>
	import { Router, Route } from 'svelte-routing';
	
	import Navbar from './components/Navbar.svelte';
	import Footer from './components/Footer.svelte';
	import Home from './views/Home.svelte';
	import Magisk from './views/Magisk.svelte';
	import SuperSU from './views/SuperSU.svelte';
	import Description from './views/Description.svelte';
	import About from './views/About.svelte';
	import Contact from './views/Contact.svelte';
	import NotFound from './views/NotFound.svelte';
</script>

<Router>
	<Navbar/>
	<div>
		<Route path="/"><Home/></Route>
		<Route path="/magisk"><Magisk/></Route>
		<Route path="/supersu"><SuperSU/></Route>
		<Route path="/description"><Description/></Route>
		<Route path="/about"><About/></Route>
		<Route path="/contact"><Contact/></Route>
		<Route component={NotFound}/>
	</div>
	<Footer/>
</Router>