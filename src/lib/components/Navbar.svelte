<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let navbar: HTMLElement;
	let isScrolled = false;

	onMount(() => {
		const handleScroll = () => {
			const scrollY = window.scrollY;
			isScrolled = scrollY > 50;

			if (navbar) {
				gsap.to(navbar, {
					backgroundColor: isScrolled
						? 'rgba(15, 23, 42, 0.95)'
						: 'rgba(15, 23, 42, 0)',
					backdropFilter: isScrolled ? 'blur(10px)' : 'blur(0px)',
					borderBottom: isScrolled
						? '1px solid rgba(148, 163, 184, 0.1)'
						: '1px solid rgba(148, 163, 184, 0)',
					duration: 0.3,
					ease: 'power2.out'
				});
			}
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<nav
	bind:this={navbar}
	class="fixed top-0 left-0 right-0 z-50 py-4 px-4 md:px-8 transition-all duration-300"
>
	<div class="max-w-7xl mx-auto flex items-center justify-between">
		<!-- Logo -->
		<div class="flex items-center gap-3 group">
			<div
				class="w-10 h-10 rounded-full bg-gradient-to-br from-pink-500 to-blue-600 flex items-center justify-center font-black text-white group-hover:scale-110 transition-transform"
			>
				P
			</div>
			<span class="font-black text-xl hidden sm:inline">POLLARIS</span>
		</div>

		<!-- Nav Links -->
		<div class="hidden md:flex gap-8">
			<a href="#emissions" class="text-slate-300 hover:text-pink-400 transition-colors font-medium">
				Émissions
			</a>
			<a href="#podcasts" class="text-slate-300 hover:text-pink-400 transition-colors font-medium">
				Podcasts
			</a>
			<a href="#equipe" class="text-slate-300 hover:text-pink-400 transition-colors font-medium">
				Équipe
			</a>
		</div>

		<!-- CTA Button -->
		<button
			class="px-6 py-2 bg-gradient-to-r from-pink-500 to-pink-600 text-white font-bold rounded-lg hover:shadow-lg hover:shadow-pink-500/50 transition-all duration-200"
		>
			En direct
		</button>
	</div>
</nav>
