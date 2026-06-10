<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let navbar: HTMLElement;
	let mobileMenu: HTMLElement;
	let isScrolled = false;
	let isMobileMenuOpen = false;

	const toggleMobileMenu = () => {
		isMobileMenuOpen = !isMobileMenuOpen;
		if (mobileMenu) {
			gsap.to(mobileMenu, {
				maxHeight: isMobileMenuOpen ? 200 : 0,
				opacity: isMobileMenuOpen ? 1 : 0,
				duration: 0.3,
				ease: 'power2.out'
			});
		}
	};

	const closeMobileMenu = () => {
		isMobileMenuOpen = false;
		if (mobileMenu) {
			gsap.to(mobileMenu, {
				maxHeight: 0,
				opacity: 0,
				duration: 0.3,
				ease: 'power2.out'
			});
		}
	};

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
		<a href="/" class="flex items-center gap-3 group hover:opacity-80 transition-opacity" on:click={closeMobileMenu}>
			<img
				src="/assets/logo-pollaris.jpg"
				alt="Pollaris Logo"
				class="h-[3.25rem] w-[3.25rem] rounded-full object-cover group-hover:scale-110 transition-transform"
			/>
		</a>

		<!-- Desktop Nav Links -->
		<div class="hidden md:flex gap-8">
			<a href="/" class="text-slate-300 hover:text-pink-400 transition-colors font-medium">
				Accueil
			</a>
			<a href="/ligne-editoriale" class="text-slate-300 hover:text-pink-400 transition-colors font-medium">
				Ligne éditoriale
			</a>
		</div>

		<div class="flex items-center gap-4">
			<!-- CTA Button (Hidden on small screens) -->
			<button
				class="hidden sm:block px-6 py-2 bg-gradient-to-r from-pink-500 to-pink-600 text-white font-bold rounded-lg hover:scale-105 transition-all duration-200"
			>
				En direct
			</button>

			<!-- Mobile Menu Button -->
			<button
				on:click={toggleMobileMenu}
				class="md:hidden flex flex-col gap-1.5 w-8 h-8 justify-center items-center"
				aria-label="Toggle menu"
			>
				<div class="w-6 h-0.5 bg-slate-300 transition-all duration-300" style="transform: {isMobileMenuOpen ? 'rotate(45deg) translateY(8px)' : 'rotate(0)'}"></div>
				<div class="w-6 h-0.5 bg-slate-300 transition-all duration-300" style="opacity: {isMobileMenuOpen ? '0' : '1'}"></div>
				<div class="w-6 h-0.5 bg-slate-300 transition-all duration-300" style="transform: {isMobileMenuOpen ? 'rotate(-45deg) translateY(-8px)' : 'rotate(0)'}"></div>
			</button>
		</div>
	</div>

	<!-- Mobile Menu -->
	<div
		bind:this={mobileMenu}
		class="md:hidden fixed left-0 right-0 top-16 bg-slate-900/95 backdrop-blur border-b border-slate-700 overflow-hidden"
		style="max-height: 0; opacity: 0;"
	>
		<div class="px-4 py-4 space-y-3">
			<a
				href="/"
				class="block text-slate-300 hover:text-pink-400 transition-colors font-medium py-2 px-3 rounded-lg hover:bg-slate-800"
				on:click={closeMobileMenu}
			>
				Accueil
			</a>
			<a
				href="/ligne-editoriale"
				class="block text-slate-300 hover:text-pink-400 transition-colors font-medium py-2 px-3 rounded-lg hover:bg-slate-800"
				on:click={closeMobileMenu}
			>
				Ligne éditoriale
			</a>
			<button
				class="w-full px-6 py-2 bg-gradient-to-r from-pink-500 to-pink-600 text-white font-bold rounded-lg hover:scale-105 transition-all duration-200 mt-2"
			>
				En direct
			</button>
		</div>
	</div>
</nav>
