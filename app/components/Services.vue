<template>
	<section class="services" aria-labelledby="services-title">
		<div class="services__layout">
			<div class="services__text">
				<h1 id="services-title">Voir au-delà du score, comprendre vraiment le match</h1>
				<p class="services__lede">
					Un match va trop vite pour tout voir, surtout au bord du terrain. En rejouant la rencontre avec notre outil, vous visualisez clairement où votre équipe défend, où elle construit et où elle finit ses actions. Les séquences clés sont mises en avant, les zones les plus utilisées apparaissent, et vous pouvez vérifier si votre projet de jeu se retrouve vraiment sur le terrain. L’idée : partir de vos vidéos habituelles et vous donner enfin une vision objective de ce que votre équipe produit, sans passer des heures à tout revoir à l’aveugle.
				</p>
			</div>

			<div class="services__hero" aria-hidden="true"></div>

			<div class="services__thumbs" aria-hidden="true">
				<div class="services__card services__card--warm"></div>
				<div class="services__card services__card--cool"></div>
			</div>
		</div>
	</section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rethink+Sans:wght@400;600;700;800&display=swap');

.services {
	padding: 10rem 1.25rem;
	background: #ffffff;
	color: #0c0c12;
	font-family: 'Rethink Sans', system-ui, -apple-system, sans-serif;
}

.services__layout {
	--block-gap: clamp(1.5rem, 4vw, 2.25rem);
	max-width: 1400px;
	margin: 0 auto;
	display: grid;
	grid-template-columns: 1.35fr 0.65fr;
	grid-template-rows: auto auto;
	grid-template-areas:
		"text hero"
		"thumbs hero";
	column-gap: var(--block-gap);
	row-gap: clamp(1.5rem, 4vw, 2.25rem);
	align-items: start;
}

.services__text {
	grid-area: text;
	display: grid;
	gap: 1rem;
}

.services__text h1 {
	margin: 0;
	font-size: clamp(2rem, 3vw, 2.6rem);
	line-height: 1.05;
	letter-spacing: -0.01em;
	font-weight: 800;
	max-width: 820px;
}

.services__lede {
	margin: 0;
	max-width: 820px;
	line-height: 1.55;
	color: #222330;
	font-size: 1rem;
}

.services__hero {
	grid-area: hero;
	width: 100%;
	height: 100%;
	min-height: 660px;
	border-radius: 18px;
	background: url('@/assets/img/Frame 21.png') center/cover no-repeat;
	position: relative;
	overflow: hidden;
}

.services__thumbs {
	grid-area: thumbs;
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
	gap: var(--block-gap);
	align-self: stretch;
}

.services__card {
	border-radius: 18px;
	min-height: 200px;
	background-size: cover;
	background-position: center;
	overflow: hidden;
	position: relative;
}

.services__card::after {
	content: "";
	position: absolute;
	inset: 0;
	background: linear-gradient(180deg, rgba(0, 0, 0, 0.12), transparent 60%);
}

.services__card--warm {
	background: url('@/assets/img/Frame 19.png') center/cover no-repeat;
}

.services__card--cool {
	background: url('@/assets/img/Frame 20.png') center/cover no-repeat;
}

@media (max-width: 1024px) {
	.services__layout {
		grid-template-columns: 1fr;
		grid-template-rows: auto 320px auto;
		grid-template-areas:
			"text"
			"hero"
			"thumbs";
	}

	.services__hero {
		min-height: 320px;
	}
}

@media (max-width: 640px) {
	.services {
		padding: 4rem 1.25rem;
	}

	.services__text h1 {
		font-size: clamp(1.8rem, 8vw, 2.2rem);
	}

	.services__thumbs {
		grid-template-columns: 1fr;
		gap: 1.5rem;
	}
    
    .services__card {
        min-height: 180px;
    }
}
</style>