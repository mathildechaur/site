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
	class="relative h-screen flex items-center justify-center overflow-hidden bg-gradient-to-b from-slate-950 via-slate-900 to-slate-800"
>
	<!-- Background elements -->
	<div class="absolute inset-0 overflow-hidden">
		<div
			class="absolute top-20 right-20 w-72 h-72 bg-pink-500 rounded-full mix-blend-screen opacity-20 blur-3xl animate-pulse"
		></div>
		<div
			class="absolute bottom-40 left-20 w-96 h-96 bg-blue-600 rounded-full mix-blend-screen opacity-20 blur-3xl animate-pulse"
			style="animation-delay: 1s"
		></div>
	</div>

	<!-- Content -->
	<div class="relative z-10 text-center px-4 max-w-4xl">
		<div class="mb-8 inline-block">
			<span
				class="inline-block text-6xl animate-bounce"
				style="animation-duration: 2s"
			>
				🎙️
			</span>
		</div>

		<h1
			bind:this={titleRef}
			class="text-6xl md:text-8xl font-black text-white mb-6 leading-tight"
			style="font-family: system-ui, -apple-system, sans-serif; letter-spacing: -2px;"
		>
			POLLARIS
		</h1>

		<p
			bind:this={subtitleRef}
			class="text-xl md:text-3xl text-slate-300 font-light mb-12"
		>
			La radio qui vous guide
		</p>

		<div class="flex flex-col sm:flex-row gap-4 justify-center">
			<button
				class="px-8 py-4 bg-gradient-to-r from-pink-500 to-pink-600 text-white font-bold rounded-xl hover:scale-105 transition-transform duration-200 shadow-lg"
			>
				Écouter en direct
			</button>
			<button
				class="px-8 py-4 bg-slate-700/50 text-white font-bold rounded-xl border border-slate-600 hover:border-pink-500 transition-colors duration-200"
			>
				Découvrir
			</button>
		</div>
	</div>

	<!-- Bottom indicator -->
	<div class="absolute bottom-8 left-1/2 -translate-x-1/2 z-10">
		<div class="animate-bounce" style="animation-duration: 2s">
			<svg class="w-6 h-6 text-pink-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
			</svg>
		</div>
	</div>
</div>
