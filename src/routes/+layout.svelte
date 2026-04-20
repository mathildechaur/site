<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import Navbar from '$lib/components/Navbar.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
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
