<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	interface Props {
		title?: string;
		subtitle?: string;
		color?: string;
		emoji?: string;
		dataAnimate?: boolean;
	}

	let { title = 'Title', subtitle = 'Subtitle', color = 'bg-blue-600', emoji = '🎵', dataAnimate = false }: Props = $props();

	let card: HTMLElement;

	onMount(() => {
		if (card && dataAnimate) {
			gsap.from(card, {
				opacity: 0,
				y: 30,
				duration: 0.8,
				ease: 'power2.out'
			});
		}

		// Hover animation
		const tl = gsap.timeline({ paused: true });
		tl.to(
			card,
			{
				y: -10,
				duration: 0.3,
				ease: 'power2.out'
			},
			0
		).to(
			card?.querySelector('[data-icon]'),
			{
				scale: 1.2,
				rotation: 5,
				duration: 0.3,
				ease: 'power2.out'
			},
			0
		);

		card?.addEventListener('mouseenter', () => tl.play());
		card?.addEventListener('mouseleave', () => tl.reverse());
	});
</script>

<div
	bind:this={card}
	class="{color} rounded-2xl p-6 md:p-8 text-white shadow-2xl hover:shadow-3xl transition-shadow duration-300 cursor-pointer group"
>
	<div class="flex items-start justify-between mb-6">
		<div>
			<p class="text-white/70 text-xs font-semibold uppercase tracking-wider mb-1">
				{subtitle}
			</p>
			<h3 class="text-2xl md:text-3xl font-black leading-tight">
				{title}
			</h3>
		</div>
		<span class="text-4xl" data-icon>{emoji}</span>
	</div>

	<div class="flex items-center justify-between">
		<button
			title="Jouer"
			class="w-12 h-12 rounded-full bg-white/20 hover:bg-white/30 text-white flex items-center justify-center transition-colors duration-200 group-hover:bg-white/40"
		>
			<svg class="w-5 h-5 ml-0.5" fill="currentColor" viewBox="0 0 24 24">
				<path d="M8 5v14l11-7z" />
			</svg>
		</button>
		<span class="text-xs font-semibold text-white/60">PLAY</span>
	</div>
</div>
