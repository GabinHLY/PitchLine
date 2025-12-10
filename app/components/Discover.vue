<template>
	<section id="discover" class="discover">
		<div class="hero">
			<div class="hero__backdrop" aria-hidden="true"></div>
			<div class="hero__content">
				<h1>Transformez vos vidéos de match en vraie analyse tactique</h1>
				<p class="hero__lede">
					Déposez la vidéo, obtenez des stats claires, des zones d’occupation et des pistes d’ajustements pour chaque joueur. Pensé pour les coachs et analystes de football amateur à semi-pro.
				</p>
				<button class="btn btn--outline">En savoir plus</button>
			</div>
		</div>

		<div class="panel-shell">
			<div class="panel-row">
				<article class="panel">
					<h2>Découvrez la première version de l’assistant vidéo</h2>
					<p class="panel__body">
						La première version de l’outil se concentre sur l’essentiel : vous partez d’une simple vidéo de match et vous la transformez en matière exploitable pour vos analyses. Après avoir importé votre fichier, vous pouvez revoir le match dans une interface dédiée et placer des tags aux moments clés : récupérations de balle, tirs, pertes, entrées dans le dernier tiers, situations de pressing… Chaque événement est enregistré avec le temps exact, la zone du terrain et le joueur concerné. En quelques minutes, vous disposez d’une timeline structurée qui remplace le bloc-notes ou les pauses incessantes sur la barre de lecture.
					</p>
					<p class="panel__body">
						À partir de ces tags, la V1 génère déjà un premier niveau d’analyse : nombre d’actions offensives et défensives, répartition des événements par zones, séquences à fort impact, implication de chaque joueur dans le jeu. Vous pouvez revenir immédiatement sur une situation précise, préparer vos retours vidéo avec l’équipe et identifier les tendances du match sans devoir recompter tout à la main. Ce n’est pas encore du tracking automatique, mais c’est un gain de temps énorme pour structurer vos observations et poser les bases d’une analyse tactique plus poussée.
					</p>
					<button class="btn btn--solid">Tester la démo</button>
				</article>

				<div class="visual">
					<div class="visual__frame">
						<div class="visual__placeholder" aria-hidden="true"></div>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rethink+Sans:ital,wght@0,400..800;1,400..800&display=swap');

:global(body) {
	margin: 0;
	background: #ffffff;
	color: #0f172a;
	font-family: 'Rethink Sans', system-ui, -apple-system, sans-serif;
}

.discover {
	min-height: 100vh;
	display: flex;
	flex-direction: column;
	gap: 2.5rem;
	padding: 15rem 1.5rem 15rem;
	background:
		linear-gradient(180deg, rgba(4, 7, 13, 0.65) 0%, rgba(4, 7, 13, 0.82) 100%),
		radial-gradient(circle at 20% 20%, rgba(79, 209, 255, 0.12), transparent 38%),
		radial-gradient(circle at 80% 10%, rgba(74, 244, 99, 0.14), transparent 40%),
		url("@/assets/img/background.png") center/cover fixed;
	color: #f4f7fb;
}

.hero {
	position: relative;
	border-radius: 0;
	overflow: hidden;
	min-height: 420px;
	display: flex;
	align-items: center;
	justify-content: center;
	background: transparent;
	box-shadow: none;
}

.hero__backdrop {
	position: absolute;
	inset: 0;
	filter: blur(1px) saturate(1.05);
	transform: scale(1.03);
	z-index: 0;
}

.hero__content {
	position: relative;
	z-index: 2;
	text-align: center;
	max-width: 880px;
	padding: 2rem 2.5rem;
	display: grid;
	gap: 1rem;
	justify-items: center;
}

.hero__kicker {
	margin: 0;
	text-transform: uppercase;
	letter-spacing: 0.08em;
	font-size: 0.85rem;
	color: #9fe7ff;
	font-weight: 700;
}

.hero h1 {
	margin: 0;
	font-size: clamp(2.4rem, 4vw, 3rem);
	line-height: 1.05;
	letter-spacing: -0.02em;
    font-weight: 800;
}

.hero__lede {
	margin: 0;
	color: #d8e2f0;
	font-size: 1.05rem;
	line-height: 1.6;
	max-width: 720px;
	margin-inline: auto;
}

.btn {
	display: inline-flex;
	align-items: center;
	justify-content: center;
	gap: 0.5rem;
	padding: 0.7rem 1.35rem;
	border-radius: 999px;
	font-weight: 700;
	font-size: 0.95rem;
	border: 1.5px solid transparent;
	transition: transform 140ms ease, box-shadow 140ms ease, background 180ms ease, border-color 180ms ease;
	width: fit-content;
}

.btn--outline {
	background: rgba(255, 255, 255, 0.07);
	border-color: rgba(255, 255, 255, 0.3);
	color: #f6fbff;
	box-shadow: 0 12px 22px rgba(0, 0, 0, 0.2);
}

.btn--outline:hover {
	transform: translateY(-1px);
	border-color: #9fe7ff;
	box-shadow: 0 18px 32px rgba(0, 0, 0, 0.22);
}

.panel-row {
	display: grid;
	grid-template-columns: repeat(2, minmax(0, 1fr));
	gap: 1.25rem;
	align-items: stretch;
	max-width: 1200px;
	margin: 0 auto;
}

.panel-shell {
	background: rgba(5, 8, 13, 0.82);
	border: 1px solid rgba(255, 255, 255, 0.06);
	box-shadow: 0 18px 36px rgba(0, 0, 0, 0.28);
	border-radius: 28px;
	padding: 1.35rem;
	margin: 0 auto 1.5rem;
}

.panel {
	background: transparent;
	border: none;
	box-shadow: none;
	border-radius: 24px;
	padding: 2rem;
	display: grid;
	gap: 0.9rem;
}

.panel__eyebrow {
	margin: 0;
	text-transform: uppercase;
	letter-spacing: 0.12em;
	font-size: 0.8rem;
	color: #8bd6ff;
	font-weight: 700;
}

.panel h2 {
	margin: 0;
	font-size: 1.6rem;
	line-height: 1.2;
}

.panel__body {
	margin: 0;
	color: #d1d8e4;
	line-height: 1.6;
	font-size: 0.98rem;
}

.btn--solid {
	background: #70ED70;
	color: #05120b;
	justify-self: start;
}

.btn--solid:hover {
	transform: translateY(-1px);
}

.visual {
	position: relative;
	display: grid;
	grid-template-rows: 1fr;
	justify-items: stretch;
	align-items: stretch;
	gap: 0.75rem;
}

.visual__frame {
	width: 100%;
	height: 100%;
	border-radius: 18px;
	padding: 0;
	background: transparent;
	border: none;
	box-shadow: none;
	display: flex;
}

.visual__placeholder {
	width: 100%;
	height: 100%;
	background: #4af463;
	border-radius: 18px;
}

.visual__caption {
	margin: 0;
	color: #9fb4cc;
	font-size: 0.95rem;
}

@media (max-width: 1080px) {
	.discover {
		padding: 8rem 1.5rem 8rem;
	}

	.panel-row {
		grid-template-columns: 1fr;
	}

	.panel {
		order: 2;
	}

	.visual {
		order: 1;
		min-height: 300px;
	}
}

@media (max-width: 720px) {
	.discover {
		padding: 6rem 1rem 4rem;
		background-attachment: scroll;
	}

	.hero {
		min-height: auto;
		padding: 2rem 0;
	}

	.hero__content {
		padding: 1.5rem 0.5rem;
		gap: 0.85rem;
	}

	.hero h1 {
		font-size: clamp(2rem, 8vw, 2.5rem);
	}

	.panel {
		padding: 1.5rem;
	}
}
</style>
