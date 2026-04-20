<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import PodcastCard from '$lib/components/PodcastCard.svelte';
	import HeroSection from '$lib/components/HeroSection.svelte';
	import FeaturedShow from '$lib/components/FeaturedShow.svelte';
	import ArtistCarousel from '$lib/components/ArtistCarousel.svelte';

	let container: HTMLElement;

	onMount(() => {
		// Animation d'entrée au chargement
		gsap.from(container.querySelectorAll('[data-animate]'), {
			duration: 0.8,
			opacity: 0,
			y: 30,
			stagger: 0.1,
			ease: 'power2.out'
		});
	});
</script>

<div bind:this={container} class="min-h-screen bg-linear-to-b from-slate-900 via-slate-900 to-slate-800">
	<!-- Hero Section -->
	<HeroSection />

	<!-- Main Content -->
	<main class="relative px-4 md:px-8 py-16">
		<!-- Bento Grid -->
		<div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-6 auto-rows-max">
			<!-- Large Featured Card (1) -->
			<div class="md:col-span-2 md:row-span-2" data-animate>
				<FeaturedShow />
			</div>

			<!-- Stats Card (2) -->
			<div
				class="bg-linear-to-br from-blue-600 to-blue-700 rounded-2xl p-8 text-white shadow-2xl hover:shadow-3xl transition-shadow"
				data-animate
			>
				<div class="h-full flex flex-col justify-between">
					<p class="text-sm font-medium text-blue-200 mb-4">STATISTIQUES</p>
					<div class="block">
						<p class="text-5xl font-black mb-2">127K</p>
						<p class="text-lg text-blue-100">Auditeurs mensuels</p>
					</div>
				</div>
			</div>

			<!-- Emission Card (3) -->
			<PodcastCard
				title="VOICES"
				subtitle="Stories & Talks"
				color="bg-pink-500"
				emoji="🎤"
				dataAnimate={true}
			/>

			<!-- Show Card (4) -->
			<PodcastCard
				title="BEATS"
				subtitle="Electronic Mix"
				color="bg-blue-600"
				emoji="♫"
				dataAnimate={true}
			/>

			<!-- Call to Action (5) -->
			<div
				class="md:col-span-2 bg-linear-to-r from-pink-500 to-pink-600 rounded-2xl p-12 text-white shadow-2xl overflow-hidden relative group"
				data-animate
			>
				<div class="absolute inset-0 bg-linear-to-r from-blue-600 to-blue-700 opacity-0 group-hover:opacity-20 transition-opacity duration-300"></div>
				<div class="relative z-10">
					<h3 class="text-3xl md:text-4xl font-black mb-4">Crée ton podcast</h3>
					<p class="text-pink-100 text-lg mb-6">Rejoins notre communauté de créateurs</p>
					<button
						class="bg-white text-pink-600 font-bold px-8 py-3 rounded-xl hover:scale-105 transition-transform duration-200 shadow-lg"
					>
						Démarrer
					</button>
				</div>
			</div>

			<!-- Recent Episodes (6) -->
			<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700" data-animate>
				<p class="text-xs font-semibold text-slate-400 mb-4">DERNIERS</p>
				<div class="space-y-4">
					<div class="group cursor-pointer">
						<p class="text-white font-bold group-hover:text-pink-400 transition-colors">Épisode 15</p>
						<p class="text-xs text-slate-400">Hier</p>
					</div>
					<div class="group cursor-pointer">
						<p class="text-white font-bold group-hover:text-pink-400 transition-colors">Épisode 14</p>
						<p class="text-xs text-slate-400">Il y a 2 jours</p>
					</div>
					<div class="group cursor-pointer">
						<p class="text-white font-bold group-hover:text-pink-400 transition-colors">Épisode 13</p>
						<p class="text-xs text-slate-400">Il y a 1 semaine</p>
					</div>
				</div>
			</div>
		</div>
	</main>

	<!-- Artist Carousel Section -->
	<ArtistCarousel />
</div>
