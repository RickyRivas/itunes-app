<script>
	import Header from '../lib/Header.svelte';
	import global from '../app.css';
</script>

<Header />

<main>
	<slot />
</main>

<style>
	main {
		width: 100%;
		height: 100vh;
		padding-top: 7em;
	}
</style>
