<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let hero: HTMLElement;
	let titleRef: HTMLElement;
	let subtitleRef: HTMLElement;

	onMount(() => {
		// Animation du titre au chargement
		gsap.fromTo(
			titleRef,
			{ opacity: 0, y: 40 },
			{ opacity: 1, y: 0, duration: 1, ease: 'power3.out', delay: 0.2 }
		);

		gsap.fromTo(
			subtitleRef,
			{ opacity: 0, y: 30 },
			{ opacity: 1, y: 0, duration: 0.8, ease: 'power3.out', delay: 0.4 }
		);

		// Animation de scroll subtle
		const handleScroll = () => {
			const scrollY = window.scrollY;
			if (hero) {
				hero.style.transform = `translateY(${scrollY * 0.3}px)`;
			}
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<div
	bind:this={hero}
	class="relative min-h-[65vh] flex flex-col items-center justify-center overflow-hidden bg-gradient-to-b from-slate-950 via-slate-900 to-slate-800"
>
	<!-- Background -->
	<div class="absolute inset-0 bg-slate-900"></div>

	<!-- Content -->
	<div class="relative z-10 text-center px-4 max-w-4xl flex-1 flex flex-col items-center justify-center">
		<img
			bind:this={titleRef}
			src="/assets/header.png"
			alt="Pollaris"
			class="w-full max-w-xs sm:max-w-sm md:max-w-lg h-auto mx-auto mb-3 sm:mb-4"
		/>

		<p
			bind:this={subtitleRef}
			class="text-base sm:text-lg md:text-2xl text-slate-300 font-light mb-6 sm:mb-8"
		>
			La radio qui vous guide
		</p>

		<div class="flex flex-col sm:flex-row gap-4 justify-center">
			<button
				class="px-8 py-4 bg-gradient-to-r from-pink-500 to-pink-600 text-white font-bold rounded-xl hover:scale-105 transition-transform duration-200 shadow-lg"
			>
				Écouter en direct
			</button>
			<a href="#social-networks"
				class="text-center inline-block px-8 py-4 bg-slate-700/50 text-white font-bold rounded-xl border border-slate-600 hover:border-pink-500 transition-colors duration-200"
			>
				Découvrir
			</a>
		</div>
	</div>

	<!-- Bottom indicator - flux normal, en dessous des boutons -->
	<div class="relative z-10 pt-6 sm:pt-8 md:pt-10 pb-6 sm:pb-8 md:pb-10">
		<div class="animate-bounce" style="animation-duration: 2s">
			<svg class="w-6 h-6 text-pink-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
			</svg>
		</div>
	</div>
</div>
