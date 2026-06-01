<script lang="ts">
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let container: HTMLElement;

	onMount(() => {
		gsap.from(container?.querySelectorAll('[data-animate]') || [], {
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
	<div class="pt-24 sm:pt-32 px-3 sm:px-4 md:px-8 pb-12 sm:pb-16">
		<div class="max-w-4xl mx-auto text-center" data-animate>
			<h1 class="text-4xl sm:text-5xl md:text-6xl font-black mb-4 sm:mb-6 bg-gradient-to-r from-pink-400 to-blue-400 bg-clip-text text-transparent">
				Ligne Éditoriale
			</h1>
			<p class="text-base sm:text-lg md:text-xl text-slate-300 max-w-2xl mx-auto px-2">
				Découvrez nos valeurs, notre vision et notre engagement envers notre communauté
			</p>
		</div>
	</div>

	<!-- Main Content -->
	<main class="relative px-3 sm:px-4 md:px-8 py-12 sm:py-16">
		<div class="max-w-4xl mx-auto space-y-8 sm:space-y-12">
			<!-- Mission Section -->
			<section class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 sm:p-8 border border-slate-700" data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-4 text-pink-400">Notre Mission</h2>
				<p class="text-lg text-slate-300 leading-relaxed mb-4">
					Pollaris est une plateforme radio innovante dédiée à la promotion de talents émergents et à la création d'un espace où la musique, les histoires et les idées peuvent s'épanouir librement.
				</p>
				<p class="text-lg text-slate-300 leading-relaxed">
					Nous croyons au pouvoir de l'audio pour connecter, inspirer et transformer les audiences du monde entier.
				</p>
			</section>

			<!-- Values Section -->
			<section data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-6 sm:mb-8 text-pink-400">Nos Valeurs</h2>
				<div class="grid grid-cols-1 md:grid-cols-2 gap-4 sm:gap-6">
					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-5 sm:p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-pink-500 to-pink-600 flex items-center justify-center text-white font-black mb-4">
							🎨
						</div>
						<h3 class="text-lg sm:text-xl font-black mb-3 text-white">Créativité</h3>
						<p class="text-slate-300">
							Nous encourageons l'expression authentique et les contenus originaux qui reflètent la diversité des perspectives.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-blue-500 to-blue-600 flex items-center justify-center text-white font-black mb-4">
							🤝
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Communauté</h3>
						<p class="text-slate-300">
							Nous bâtissons une communauté inclusive où créateurs et auditeurs collaborent et grandissent ensemble.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-green-500 to-green-600 flex items-center justify-center text-white font-black mb-4">
							🔥
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Innovation</h3>
						<p class="text-slate-300">
							Nous explorons les nouvelles technologies et formats pour améliorer l'expérience audio et d'engagement.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-purple-500 to-purple-600 flex items-center justify-center text-white font-black mb-4">
							🌍
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Accessibilité</h3>
						<p class="text-slate-300">
							Nous rendons la création audio accessible à tous, indépendamment du niveau d'expérience ou des ressources.
						</p>
					</div>
				</div>
			</section>

			<!-- Content Policy Section -->
			<section class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 sm:p-8 border border-slate-700" data-animate>
				<h2 class="text-xl sm:text-2xl font-black mb-6 text-pink-400">Politique de Contenu</h2>
				<div class="space-y-4 text-slate-300">
					<p>
						<span class="font-bold text-white">✓ Nous encourageons :</span> La musique de qualité, les conversations authentiques, les contenus éducatifs, les perspectives diverses, et l'innovation créative.
					</p>
					<p>
						<span class="font-bold text-white">✗ Nous n'acceptons pas :</span> Le contenu haineux, les discriminations, le harcèlement, ou tout contenu violant les droits d'autrui.
					</p>
					<p class="text-sm text-slate-400 mt-6">
						Tous les créateurs acceptent nos directives communautaires lors de l'inscription.
					</p>
				</div>
			</section>

			<!-- Vision Section -->
			<section class="bg-gradient-to-r from-pink-500/20 to-blue-500/20 backdrop-blur rounded-2xl p-6 sm:p-8 border border-slate-700" data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-4 text-pink-400">Notre Vision</h2>
				<p class="text-lg text-slate-300 leading-relaxed">
					Nous envisageons Pollaris comme la plateforme audio incontournable pour les créateurs ambitieux et les auditeurs passionnés. Un espace où la qualité, l'authenticité et l'innovation se rencontrent pour créer des expériences audio inoubliables.
				</p>
			</section>
		</div>
	</main>
</div>
