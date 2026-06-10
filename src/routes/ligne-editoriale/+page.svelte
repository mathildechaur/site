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
			<h1 class="text-4xl sm:text-5xl md:text-6xl font-black mb-4 sm:mb-6 bg-gradient-to-r from-pink-400 to-blue-400 bg-clip-text text-transparent leading-tight">
				Ligne Éditoriale
			</h1>
			<p class="text-xl sm:text-2xl font-bold text-pink-400 mb-4">
				Pollaris, la radio qui vous guide ⭐️
			</p>
			<p class="text-base sm:text-lg md:text-xl text-slate-300 max-w-2xl mx-auto px-2">
				Un espace d'écoute et de dialogue autour d'un enjeu de société majeur. Pollaris est une webradio spécialisée dans les Violences Sexistes et Sexuelles (VSS).
			</p>
		</div>
	</div>

	<!-- Main Content -->
	<main class="relative px-3 sm:px-4 md:px-8 py-12 sm:py-16">
		<div class="max-w-4xl mx-auto space-y-8 sm:space-y-12">
			<!-- DNA Section -->
			<section class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 sm:p-8 border border-slate-700" data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-6 text-pink-400">L'ADN et la Promesse</h2>
				<div class="space-y-6">
					<div>
						<h3 class="text-xl font-bold text-white mb-2">Notre Positionnement</h3>
						<p class="text-lg text-slate-300 leading-relaxed">
							Un espace d'écoute et de dialogue autour d'un enjeu de société majeur. Pollaris est une webradio spécialisée dans les Violences Sexistes et Sexuelles (VSS).
						</p>
					</div>
				</div>
			</section>

			<!-- Mission Section -->
			<section data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-6 sm:mb-8 text-pink-400">La Mission (Nos Objectifs)</h2>
				<p class="text-lg text-slate-300 mb-6 leading-relaxed">
					L'action de Pollaris s'articule autour de trois grands piliers fondamentaux :
				</p>
				<div class="grid grid-cols-1 md:grid-cols-3 gap-4 sm:gap-6">
					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-5 sm:p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-pink-500 to-pink-600 flex items-center justify-center text-white font-black mb-4">
							📢
						</div>
						<h3 class="text-lg sm:text-xl font-black mb-3 text-white">Informer et Sensibiliser</h3>
						<p class="text-slate-300">
							Décrypter les enjeux, vulgariser les notions complexes et alerter sur les réalités des VSS.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-blue-500 to-blue-600 flex items-center justify-center text-white font-black mb-4">
							🎤
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Donner la Parole</h3>
						<p class="text-slate-300">
							Offrir une plateforme sécurisée et bienveillante pour faire entendre la voix des victimes, des experts, et des associations engagées.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-green-500 to-green-600 flex items-center justify-center text-white font-black mb-4">
							🤝
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Soutenir et Outiller</h3>
						<p class="text-slate-300">
							Partager des ressources concrètes et apporter un soutien actif à celles et ceux qui agissent au quotidien contre ces violences.
						</p>
					</div>
				</div>
			</section>

			<!-- Format Section -->
			<section data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-6 sm:mb-8 text-pink-400">Le Format (Comment nous agissons)</h2>
				<p class="text-lg text-slate-300 mb-6 leading-relaxed">
					La webradio s'appuie sur une diversité de contenus audio pour animer cet espace de dialogue :
				</p>
				<div class="grid grid-cols-1 md:grid-cols-3 gap-4 sm:gap-6">
					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-5 sm:p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-pink-500 to-pink-600 flex items-center justify-center text-white font-black mb-4">
							📻
						</div>
						<h3 class="text-lg sm:text-xl font-black mb-3 text-white">Émissions Thématiques</h3>
						<p class="text-slate-300">
							Pour ouvrir des discussions de fond sur des sujets spécifiques.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-blue-500 to-blue-600 flex items-center justify-center text-white font-black mb-4">
							💬
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Témoignages</h3>
						<p class="text-slate-300">
							Pour incarner la réalité des VSS et favoriser l'empathie.
						</p>
					</div>

					<div class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 border border-slate-700">
						<div class="w-12 h-12 rounded-full bg-gradient-to-br from-green-500 to-green-600 flex items-center justify-center text-white font-black mb-4">
							🎙️
						</div>
						<h3 class="text-xl font-black mb-3 text-white">Interviews & Échanges</h3>
						<p class="text-slate-300">
							Pour croiser les regards entre les acteurs de terrain, les professionnels et les associations.
						</p>
					</div>
				</div>
			</section>

			<!-- Ecosystem Section -->
			<section class="bg-slate-800/50 backdrop-blur rounded-2xl p-6 sm:p-8 border border-slate-700" data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-6 text-pink-400">L'Écosystème Numérique (Notre Communauté)</h2>
				<p class="text-lg text-slate-300 mb-6 leading-relaxed">
					Pollaris adopte une stratégie multiplateforme pour toucher un public large et diversifié, tout en créant une véritable communauté d'entraide :
				</p>
				<div class="space-y-4">
					<div class="bg-slate-900/50 rounded-xl p-4 border border-slate-600">
						<h3 class="text-lg font-black text-pink-400 mb-2">📸 Instagram</h3>
						<p class="text-slate-300">
							Pour la prévention visuelle, les annonces d'émissions et les formats courts (série "Les visages de la lutte").
						</p>
					</div>
					<div class="bg-slate-900/50 rounded-xl p-4 border border-slate-600">
						<h3 class="text-lg font-black text-blue-400 mb-2">f Facebook</h3>
						<p class="text-slate-300">
							Pour le partage d'articles de fond, de ressources communautaires et le relais des émissions auprès d'un public intergénérationnel.
						</p>
					</div>
					<div class="bg-slate-900/50 rounded-xl p-4 border border-slate-600">
						<h3 class="text-lg font-black text-purple-400 mb-2">🐘 Mastodon</h3>
						<p class="text-slate-300">
							Un choix fort ! Ce réseau décentralisé garantit un espace perçu comme plus safe et libre des algorithmes traditionnels, idéal pour des discussions sans filtre sur des sujets sensibles.
						</p>
					</div>
				</div>
			</section>

			<!-- Vision Section -->
			<section class="bg-gradient-to-r from-pink-500/20 to-blue-500/20 backdrop-blur rounded-2xl p-6 sm:p-8 border border-slate-700" data-animate>
				<h2 class="text-2xl sm:text-3xl font-black mb-4 text-pink-400">Notre Engagement</h2>
				<p class="text-lg text-slate-300 leading-relaxed">
					Pollaris s'engage à créer un espace sécurisé, inclusif et bienveillant où les voix des victimes, des experts et des associations peuvent être entendues. En mettant la sensibilisation et l'action au cœur de notre mission, nous contribuons à la lutte contre les Violences Sexistes et Sexuelles, un enjeu majeur de notre société.
				</p>
			</section>
		</div>
	</main>
</div>
