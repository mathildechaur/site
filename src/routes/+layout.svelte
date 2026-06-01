<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/fivicon.png';
	import Navbar from '$lib/components/Navbar.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" type="image/png" href={favicon} />
	<title>Pollaris - La radio qui vous guide</title>
</svelte:head>

<div class="bg-slate-900 text-white">
	<Navbar />
	{@render children()}
</div>

<style>
	:global(html) {
		scroll-behavior: smooth;
	}

	:global(body) {
		background-color: #0f172a;
		color: white;
	}
</style>
