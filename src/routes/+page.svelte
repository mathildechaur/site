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

			<!-- Kithara Playlist Card (4) -->
			<div class="rounded-2xl overflow-hidden text-white shadow-2xl hover:shadow-3xl transition-shadow duration-300 cursor-pointer group" style="background-color: #190B28;" data-animate>
				<div class="flex items-stretch h-full">
					<!-- Image on the left -->
					<div class="w-1/3 md:w-2/5 flex-shrink-0 overflow-hidden">
						<img src="/assets/playlist.jpg" alt="Kithara Playlist" class="w-full h-full object-cover" />
					</div>

					<!-- Content on the right -->
					<div class="flex-1 p-6 md:p-8 flex flex-col justify-between">
						<div>
							<p class="text-white/70 text-xs font-semibold uppercase tracking-wider mb-1">
								Playlist
							</p>
							<h3 class="text-2xl md:text-3xl font-black leading-tight">
								Kithara
							</h3>
						</div>

						<div class="flex items-center gap-3">
							<button
								class="w-12 h-12 rounded-full bg-white/20 hover:bg-white/30 text-white flex items-center justify-center transition-colors duration-200 group-hover:bg-white/40"
							>
								<svg class="w-5 h-5 ml-0.5" fill="currentColor" viewBox="0 0 24 24">
									<path d="M8 5v14l11-7z" />
								</svg>
							</button>
							<span class="text-xs font-semibold text-white/60">PLAY</span>
						</div>
					</div>
				</div>
			</div>

			<!-- Call to Action (5) -->
			<a
				href="https://www.mixcloud.com/Infocoml3/pollaris-webradio-interview-isabelle-proust-vss-mathilde-chaurreau/"
				target="_blank"
				rel="noopener noreferrer"
				class="md:col-span-2 bg-pink-500 rounded-2xl overflow-hidden text-white shadow-2xl hover:shadow-3xl transition-shadow duration-300 group block"
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

						<div class="flex items-center gap-3">
							<button
								class="w-12 h-12 rounded-full bg-white/20 hover:bg-white/30 text-white flex items-center justify-center transition-colors duration-200 group-hover:bg-white/40"
							>
								<svg class="w-5 h-5 ml-0.5" fill="currentColor" viewBox="0 0 24 24">
									<path d="M8 5v14l11-7z" />
								</svg>
							</button>
							<span class="text-xs font-semibold text-white/60">PLAY</span>
						</div>
					</div>
				</div>
			</a>
		</div>
	</main>

	<!-- Artist Carousel Section -->
	<ArtistCarousel />

	<!-- Social Networks Section -->
	<section id="social-networks" class="py-16 sm:py-20 md:py-24 px-3 sm:px-4 md:px-8 bg-gradient-to-b from-slate-900 to-slate-800">
		<div class="max-w-7xl mx-auto">
			<div class="text-center mb-12 sm:mb-16">
				<h2 class="text-4xl sm:text-5xl md:text-6xl font-black text-white mb-4">NOS RÉSEAUX</h2>
				<div class="w-24 sm:w-32 h-1.5 bg-gradient-to-r from-pink-500 to-blue-600 mx-auto"></div>
			</div>

			<div class="grid grid-cols-1 md:grid-cols-3 gap-6 sm:gap-8 max-w-4xl mx-auto">
				<a href="https://www.instagram.com/pollaris.webradio/" target="_blank" rel="noopener noreferrer" class="bg-gradient-to-br from-pink-500 to-purple-600 rounded-2xl p-8 text-white shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105">
					<h3 class="text-3xl sm:text-4xl font-black mb-3">📸</h3>
					<h4 class="text-2xl font-black mb-3">Instagram</h4>
					<p class="text-white/90">Suivez nos actualités, stories et contenus visuels</p>
				</a>

				<a href="https://www.facebook.com/profile.php?id=61583572569805" target="_blank" rel="noopener noreferrer" class="bg-gradient-to-br from-blue-500 to-blue-700 rounded-2xl p-8 text-white shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105">
					<h3 class="text-3xl sm:text-4xl font-black mb-3">f</h3>
					<h4 class="text-2xl font-black mb-3">Facebook</h4>
					<p class="text-white/90">Partagez et discutez avec notre communauté</p>
				</a>

				<a href="https://mastodon.social/@pollariswebradio" target="_blank" rel="noopener noreferrer" class="bg-gradient-to-br from-cyan-600 to-teal-600 rounded-2xl p-8 text-white shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105">
					<h3 class="text-3xl sm:text-4xl font-black mb-3">🐘</h3>
					<h4 class="text-2xl font-black mb-3">Mastodon</h4>
					<p class="text-white/90">Discussions décentralisées et sécurisées</p>
				</a>
			</div>
		</div>
	</section>
</div>
