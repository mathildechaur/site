<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	gsap.registerPlugin(ScrollTrigger);

	interface Artist {
		name: string;
		role: string;
		image: string;
	}

	const artists: Artist[] = [
		{ name: 'Angèle', role: 'Artiste', image: '/assets/angele.jpg' },
		{ name: 'Lisa', role: 'Artiste', image: '/assets/lisa.jpg' },
		{ name: 'Orelsan', role: 'Artiste', image: '/assets/orelsan.jpg' },
		{ name: 'Pomme', role: 'Artiste', image: '/assets/pomme-.jpeg' },
		{ name: 'Solann', role: 'Artiste', image: '/assets/solann.jpg' },
		{ name: 'Stromae', role: 'Artiste', image: '/assets/stromae.jpg' },
		{ name: 'Suzane', role: 'Artiste', image: '/assets/suzane.png' },
		{ name: 'Youssoupha', role: 'Artiste', image: '/assets/youssoupha.jpg' },
		{ name: 'Rihanna', role: 'Artiste', image: '/assets/rihanna.jpg' },
		{ name: 'Sheldon', role: 'Artiste', image: '/assets/sheldon.jpg' }
	];

	let scrollContainer: HTMLElement;
	let isScrolling = false;

	// Créer le pattern : [GRAND] [2x2 carré] [GRAND] [2x2 carré] etc
	let patternItems: Array<{ type: 'large' | 'grid'; items: Artist[] }> = $state([]);

	onMount(() => {
		// Détection du scroll horizontal avec la roulette de la souris
		const handleWheel = (e: WheelEvent) => {
			if (Math.abs(e.deltaY) > Math.abs(e.deltaX)) {
				e.preventDefault();
				if (scrollContainer) {
					scrollContainer.scrollLeft += e.deltaY;
				}
			}
		};

		scrollContainer?.addEventListener('wheel', handleWheel, { passive: false });
		// Créer les patterns
		const pattern = [];
		let artistIndex = 0;

		for (let i = 0; i < 2; i++) {
			// GRAND
			pattern.push({
				type: 'large' as const,
				items: [artists[artistIndex % artists.length]]
			});
			artistIndex++;

			// 2x2 carré (4 petits)
			const gridArtists = [];
			for (let j = 0; j < 4; j++) {
				gridArtists.push(artists[artistIndex % artists.length]);
				artistIndex++;
			}
			pattern.push({
				type: 'grid' as const,
				items: gridArtists
			});
		}

		patternItems = pattern;

		// Animation au scroll de la page
		gsap.from(scrollContainer?.querySelectorAll('[data-artist]'), {
			scrollTrigger: {
				trigger: scrollContainer,
				start: 'top 80%',
				toggleActions: 'play none none reverse'
			},
			opacity: 0,
			scale: 0.8,
			duration: 0.6,
			stagger: 0.05,
			ease: 'back.out'
		});

		return () => {
			scrollContainer?.removeEventListener('wheel', handleWheel);
		};
	});
</script>

<section class="relative py-16 sm:py-20 md:py-24 px-0 bg-gradient-to-b from-slate-900 to-slate-900">
	<!-- Title -->
	<div class="text-center mb-12 sm:mb-16 md:mb-20 px-4">
		<h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-black text-white mb-4">ARTISTES</h2>
		<div class="w-24 sm:w-32 h-1.5 bg-gradient-to-r from-pink-500 to-blue-600 mx-auto"></div>
	</div>

	<!-- Carousel Container -->
	<div class="w-full">
		<!-- Scroll Container -->
		<div
			bind:this={scrollContainer}
			class="flex gap-6 sm:gap-8 md:gap-12 lg:gap-16 overflow-x-auto pb-8 px-4 sm:px-6 md:px-24 lg:px-32 cursor-grab active:cursor-grabbing"
			style="scroll-behavior: smooth; scroll-padding: 1rem;"
		>
				{#each patternItems as patternItem, idx (idx)}
					{#if patternItem.type === 'large'}
						<!-- GRAND CERCLE -->
						<div
							data-artist
							class="flex-shrink-0 group/item"
						>
							<div
								class="relative w-40 h-40 sm:w-56 sm:h-56 md:w-72 md:h-72 lg:w-80 lg:h-80 rounded-full overflow-hidden shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105 cursor-pointer bg-gradient-to-br from-slate-800 to-slate-900"
							>
								<img
									src={patternItem.items[0].image}
									alt={patternItem.items[0].name}
									class="w-full h-full object-cover group-hover/item:scale-110 transition-transform duration-300"
								/>
								<!-- Overlay -->
								<div
									class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent opacity-0 group-hover/item:opacity-100 transition-opacity duration-300 flex items-end justify-center pb-6 sm:pb-8"
								>
									<div class="text-center">
										<p class="text-white font-bold text-base sm:text-lg md:text-xl">{patternItem.items[0].name}</p>
										<p class="text-pink-400 text-xs sm:text-sm md:text-base">{patternItem.items[0].role}</p>
									</div>
								</div>
							</div>
						</div>
					{:else}
						<!-- CARRÉ 2x2 DE PETITS CERCLES -->
						<div
							data-artist
							class="flex-shrink-0 grid grid-cols-2 gap-3 sm:gap-4 md:gap-6 lg:gap-8"
							style="width: auto; height: auto;"
						>
							{#each patternItem.items as artist (artist.name)}
								<div
									class="group/small"
								>
									<div
										class="relative w-24 h-24 sm:w-28 sm:h-28 md:w-36 md:h-36 lg:w-40 lg:h-40 rounded-full overflow-hidden shadow-xl hover:shadow-2xl transition-all duration-300 hover:scale-105 cursor-pointer bg-gradient-to-br from-slate-800 to-slate-900"
									>
										<img
											src={artist.image}
											alt={artist.name}
											class="w-full h-full object-cover group-hover/small:scale-110 transition-transform duration-300"
										/>
										<!-- Overlay -->
										<div
											class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent opacity-0 group-hover/small:opacity-100 transition-opacity duration-300 flex items-end justify-center pb-3 sm:pb-4"
										>
											<div class="text-center">
												<p class="text-white font-bold text-xs sm:text-sm md:text-base">{artist.name}</p>
												<p class="text-pink-400 text-xs sm:text-xs md:text-sm">{artist.role}</p>
											</div>
										</div>
									</div>
								</div>
							{/each}
						</div>
					{/if}
				{/each}
			</div>
	</div>
</section>

<style>
	::-webkit-scrollbar {
		display: none;
	}

	div {
		-ms-overflow-style: none;
		scrollbar-width: none;
	}
</style>
