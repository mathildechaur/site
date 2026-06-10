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
	<section class="relative py-16 sm:py-20 md:py-24 px-3 sm:px-4 md:px-8 bg-gradient-to-b from-slate-900 to-slate-800">
		<div class="max-w-7xl mx-auto">
			<div class="text-center mb-12 sm:mb-16 md:mb-20">
				<h2 class="text-4xl sm:text-5xl md:text-6xl font-black text-white mb-4">NOS RÉSEAUX</h2>
				<div class="w-24 sm:w-32 h-1.5 bg-gradient-to-r from-pink-500 to-blue-600 mx-auto"></div>
			</div>

			<div class="grid grid-cols-1 md:grid-cols-2 gap-6 sm:gap-8 max-w-2xl mx-auto">
				<!-- Instagram Card -->
				<a
					href="https://www.instagram.com/pollaris.webradio/"
					target="_blank"
					rel="noopener noreferrer"
					class="group bg-gradient-to-br from-pink-500 to-purple-600 rounded-2xl p-8 text-white shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105"
					data-animate
				>
					<div class="flex items-center justify-between mb-4">
						<h3 class="text-3xl font-black">Instagram</h3>
						<svg class="w-12 h-12 opacity-80 group-hover:opacity-100 transition-opacity" fill="currentColor" viewBox="0 0 24 24">
							<path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.266.07 1.646.07 4.85s-.012 3.584-.07 4.85c-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849s.013-3.583.07-4.849c.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.646-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zM5.838 12a6.162 6.162 0 1 1 12.324 0 6.162 6.162 0 0 1-12.324 0zM12 16a4 4 0 1 1 0-8 4 4 0 0 1 0 8zm4.965-10.322a1.44 1.44 0 1 1 2.881.001 1.44 1.44 0 0 1-2.881-.001z"/>
						</svg>
					</div>
					<p class="text-white/80 group-hover:text-white transition-colors">
						Suivez nos actualités, stories et contenus visuels
					</p>
				</a>

				<!-- Mastodon Card -->
				<a
					href="https://mastodon.social/@pollariswebradio"
					target="_blank"
					rel="noopener noreferrer"
					class="group bg-gradient-to-br from-blue-600 to-cyan-600 rounded-2xl p-8 text-white shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105"
					data-animate
				>
					<div class="flex items-center justify-between mb-4">
						<h3 class="text-3xl font-black">Mastodon</h3>
						<svg class="w-12 h-12 opacity-80 group-hover:opacity-100 transition-opacity" fill="currentColor" viewBox="0 0 24 24">
							<path d="M23.268 5.313c.35-2.615.686-6.268-1.276-7.039C19.881.842 19.5 4.6 19.5 4.6c-.784-.053-1.6-.173-2.473-.365 2.201-.988 4.408.753 4.238 2.65-.184 2.522-2.929 4.785-5.666 4.978 3.215.462 4.552 3.456 3.596 5.75-.531 1.624-1.956 2.471-3.368 2.471a3.53 3.53 0 0 1-.946-.135c3.477.76 4.844 3.82 4.021 6.031-.connector 1.624-1.956 2.471-3.368 2.471-.5 0-.952-.091-1.406-.23 2.514.939 5.868 1.24 8.276-.424 3.282-2.188 3.657-7.402.661-10.726.19 1.214.738 2.337 1.341 2.62 1.557.618 3.606.406 5.355-1.235 2.27-2.156 2.613-5.793 2.9-7.781z"/>
						</svg>
					</div>
					<p class="text-white/80 group-hover:text-white transition-colors">
						Discussions décentralisées et sécurisées
					</p>
				</a>
			</div>
		</div>
	</section>
</div>
