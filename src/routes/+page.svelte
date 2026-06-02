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
	<main class="relative px-3 sm:px-4 md:px-8 py-12 sm:py-16">
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
				title="Micro trottoir"
				subtitle="Stories & Talks"
				color="bg-pink-500"
				dataAnimate={true}
				href="https://www.mixcloud.com/Infocoml3/pollaris-webradio-micro-trottoir-vss-mathilde-chaurreau/"
				image="/assets/micro-trottoir-minia.jpg"
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
				class="md:col-span-2 bg-pink-500 rounded-2xl overflow-hidden text-white shadow-2xl hover:shadow-3xl transition-shadow duration-300 group"
				data-animate
			>
				<div class="flex items-stretch h-full">
					<!-- Image on the left -->
					<div class="w-1/3 md:w-2/5 flex-shrink-0 overflow-hidden">
						<img src="/assets/interview.jpg" alt="interview Isabelle Proust Sauviac" class="w-full h-full object-cover" />
					</div>

					<!-- Content on the right -->
					<div class="flex-1 p-6 md:p-8 flex flex-col justify-between">
						<div>
							<p class="text-white/70 text-xs font-semibold uppercase tracking-wider mb-1">
								Interview
							</p>
							<h3 class="text-2xl md:text-3xl font-black leading-tight">
								Isabelle Proust Sauviac
							</h3>
						</div>

						<button
							class="w-12 h-12 rounded-full bg-white/20 hover:bg-white/30 text-white flex items-center justify-center transition-colors duration-200 group-hover:bg-white/40"
						>
							<svg class="w-5 h-5 ml-0.5" fill="currentColor" viewBox="0 0 24 24">
								<path d="M8 5v14l11-7z" />
							</svg>
						</button>
					</div>
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
