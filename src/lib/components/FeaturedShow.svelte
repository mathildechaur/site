<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let card: HTMLElement;
	let playButton: HTMLElement;
	let isHovering = false;

	onMount(() => {
		// Hover animation
		card?.addEventListener('mouseenter', () => {
			isHovering = true;
			gsap.to(playButton, {
				scale: 1.2,
				duration: 0.3,
				ease: 'power2.out'
			});
		});

		card?.addEventListener('mouseleave', () => {
			isHovering = false;
			gsap.to(playButton, {
				scale: 1,
				duration: 0.3,
				ease: 'power2.out'
			});
		});
	});

	const handlePlayClick = () => {
		// Animation du bouton
		gsap.fromTo(
			playButton,
			{ scale: 0.8 },
			{ scale: 1, duration: 0.2, ease: 'back.out' }
		);
	};
</script>

<div
	bind:this={card}
	class="relative h-full bg-gradient-to-br from-blue-600 to-blue-700 rounded-3xl overflow-hidden shadow-2xl hover:shadow-3xl transition-shadow duration-300 group"
>
	<!-- Background image or gradient -->
	<div class="absolute inset-0 bg-gradient-to-t from-slate-900/80 via-slate-900/20 to-transparent"></div>

	<!-- Content -->
	<div class="relative h-full p-6 sm:p-8 md:p-12 flex flex-col justify-between">
		<div>
			<p class="text-blue-200 text-xs sm:text-sm font-semibold uppercase tracking-wider mb-2">
				En ce moment
			</p>
			<h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl font-black text-white mb-2 leading-tight">
				Pollaris<br />
				c'est quoi ?
			</h2>
			<p class="text-blue-100 text-sm sm:text-base md:text-lg leading-relaxed max-w-sm mt-4 sm:mt-6">
				Une radio qui vous guide à travers des histoires inspirantes, des débats captivants
				et des découvertes musicales.
			</p>
		</div>

		<!-- Play Button -->
		<div class="flex items-end justify-between gap-4">
			<button
				bind:this={playButton}
				onclick={handlePlayClick}
				title="Écouter"
				class="w-12 sm:w-14 md:w-16 h-12 sm:h-14 md:h-16 rounded-full bg-pink-500 hover:bg-pink-600 text-white flex items-center justify-center shadow-xl transition-colors duration-200 flex-shrink-0"
			>
				<svg class="w-6 sm:w-7 md:w-8 h-6 sm:h-7 md:h-8 ml-1" fill="currentColor" viewBox="0 0 24 24">
					<path d="M8 5v14l11-7z" />
				</svg>
			</button>

			<div class="text-right">
				<p class="text-pink-300 font-semibold text-xs sm:text-sm">DIRECT</p>
				<p class="text-white font-black text-lg sm:text-xl md:text-2xl">LIVE</p>
			</div>
		</div>
	</div>

	<!-- Hover effect -->
	<div
		class="absolute inset-0 bg-gradient-to-br from-pink-500/0 to-pink-500/0 group-hover:from-pink-500/10 group-hover:to-pink-500/5 transition-all duration-300 pointer-events-none"
	></div>
</div>
