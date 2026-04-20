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
		{ name: 'Studio', role: 'Voice', image: '/assets/post2.jpg' },
		{ name: 'Céline', role: 'Animatrice', image: '/assets/Notre-équipe.jpg' },
		{ name: 'Matéo', role: 'DJ', image: '/assets/post1-part1.jpg' },
		{ name: 'Mathilde', role: 'Créative', image: '/assets/post3-part1.jpg' },
		{ name: 'Guest', role: 'Podcast', image: '/assets/citation.jpg' },
		{ name: 'Voices', role: 'Mix', image: '/assets/post3-part2.jpg' },
		{ name: 'Podcast', role: 'Story', image: '/assets/post1-part2.jpg' },
		{ name: 'Mix', role: 'Beat', image: '/assets/post3-part3.jpg' }
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

		for (let i = 0; i < 6; i++) {
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

<section class="relative py-24 px-0 md:px-0 bg-gradient-to-b from-slate-900 to-slate-900">
	<!-- Title -->
	<div class="text-center mb-20 px-4">
		<h2 class="text-5xl md:text-7xl font-black text-white mb-4">ARTISTES</h2>
		<div class="w-32 h-1.5 bg-gradient-to-r from-pink-500 to-blue-600 mx-auto"></div>
	</div>

	<!-- Carousel Container -->
	<div class="w-full">
		<!-- Scroll Container -->
		<div
			bind:this={scrollContainer}
			class="flex gap-12 md:gap-16 overflow-x-auto pb-8 px-24 md:px-32 cursor-grab active:cursor-grabbing"
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
								class="relative w-56 h-56 md:w-80 md:h-80 rounded-full overflow-hidden shadow-2xl hover:shadow-3xl transition-all duration-300 hover:scale-105 cursor-pointer bg-gradient-to-br from-slate-800 to-slate-900"
							>
								<img
									src={patternItem.items[0].image}
									alt={patternItem.items[0].name}
									class="w-full h-full object-cover group-hover/item:scale-110 transition-transform duration-300"
								/>
								<!-- Overlay -->
								<div
									class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent opacity-0 group-hover/item:opacity-100 transition-opacity duration-300 flex items-end justify-center pb-8"
								>
									<div class="text-center">
										<p class="text-white font-bold text-lg md:text-xl">{patternItem.items[0].name}</p>
										<p class="text-pink-400 text-sm md:text-base">{patternItem.items[0].role}</p>
									</div>
								</div>
							</div>
						</div>
					{:else}
						<!-- CARRÉ 2x2 DE PETITS CERCLES -->
						<div
							data-artist
							class="flex-shrink-0 grid grid-cols-2 gap-6 md:gap-8"
							style="width: auto; height: auto;"
						>
							{#each patternItem.items as artist (artist.name)}
								<div
									class="group/small"
								>
									<div
										class="relative w-32 h-32 md:w-40 md:h-40 rounded-full overflow-hidden shadow-xl hover:shadow-2xl transition-all duration-300 hover:scale-105 cursor-pointer bg-gradient-to-br from-slate-800 to-slate-900"
									>
										<img
											src={artist.image}
											alt={artist.name}
											class="w-full h-full object-cover group-hover/small:scale-110 transition-transform duration-300"
										/>
										<!-- Overlay -->
										<div
											class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent opacity-0 group-hover/small:opacity-100 transition-opacity duration-300 flex items-end justify-center pb-4"
										>
											<div class="text-center">
												<p class="text-white font-bold text-sm">{artist.name}</p>
												<p class="text-pink-400 text-xs">{artist.role}</p>
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
