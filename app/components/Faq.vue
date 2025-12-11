<template>
	<section class="faq" aria-labelledby="faq-title">
		<div class="faq__shell">
			<h2 id="faq-title">Vos questions les plus fréquentes :</h2>

			<ul class="faq__list">
				<li v-for="(item, index) in items" :key="item.question" class="faq__item">
					<button
						class="faq__question"
						type="button"
						:id="`faq-question-${index}`"
						:aria-expanded="openIndex === index"
						:aria-controls="`faq-panel-${index}`"
						@click="toggle(index)"
					>
						<span>{{ item.question }}</span>
						<span class="faq__icon" :class="{ 'faq__icon--open': openIndex === index }" aria-hidden="true"></span>
					</button>

					<Transition name="accordion">
						<div
							v-if="openIndex === index"
							class="faq__answer"
							:id="`faq-panel-${index}`"
							role="region"
							:aria-labelledby="`faq-question-${index}`"
						>
							<p>{{ item.answer }}</p>
						</div>
					</Transition>
				</li>
			</ul>
		</div>
	</section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

type FaqItem = {
	question: string;
	answer: string;
};

const items: FaqItem[] = [
	{
		question: 'Où puis-je analyser mes matchs ?',
		answer:
			'Vous pouvez analyser vos matchs directement depuis votre tableau de bord Pitchline. Importez vos données, et la plateforme génère automatiquement vos stats clés, votre composition, vos insights tactiques et l\'historique de vos performances.',
	},
	{
		question: "Comment importer les données d'un match ?",
		answer:
			'Ajoutez la vidéo du match et les feuilles de stats disponibles. Pitchline synchronise et enrichit ces données pour produire des visualisations prêtes à l\'analyse.',
	},
	{
		question: 'Pitchline est-il compatible avec mobile et tablette ?',
		answer: 'Oui, l\'interface est optimisée pour mobile et tablette pour consulter ou partager vos analyses en déplacement.',
	},
	{
		question: 'Puis-je gérer plusieurs équipes ?',
		answer: 'Vous pouvez créer autant d\'équipes que nécessaire, avec des espaces dédiés pour vos effectifs, vidéos et statistiques.',
	},
	{
		question: 'Les joueurs ont-ils accès aux analyses ?',
		answer: 'Vous choisissez ce que vous partagez. Invitez vos joueurs et staff avec des droits adaptés pour diffuser les comptes rendus ou les séquences clés.',
	},
	{
		question: 'Quelles données sont analysées ?',
		answer: 'Possession, zones d\'attaque, séquences clés, efficacité offensive/défensive, contributions individuelles et comparatifs match après match.',
	},
	{
		question: 'Pitchline permet-il de préparer les matchs ?',
		answer: 'Oui, créez des plans de jeu, identifiez les points forts/faiblesses adverses et partagez les focus tactiques avec votre groupe.',
	},
];

const openIndex = ref<number | null>(0);

const toggle = (index: number) => {
	openIndex.value = openIndex.value === index ? null : index;
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rethink+Sans:wght@500;600;700&display=swap');

.faq {
	position: relative;
	padding: clamp(3rem, 6vw, 5rem) 1.25rem;
	overflow: hidden;
	font-family: 'Rethink Sans', system-ui, -apple-system, sans-serif;
}

.faq::before {
	content: '';
	position: absolute;
	inset: 0;
	background:
		repeating-linear-gradient(
			90deg,
			rgba(255, 255, 255, 0.5) 0,
			rgba(255, 255, 255, 0.5) 1px,
			transparent 1px,
			transparent 90px
		),
		repeating-linear-gradient(
			0deg,
			rgba(255, 255, 255, 0.35) 0,
			rgba(255, 255, 255, 0.35) 1px,
			transparent 1px,
			transparent 120px
		);
	opacity: 0.8;
	pointer-events: none;
}

.faq__shell {
	position: relative;
	max-width: 1150px;
	margin: 0 auto;
	border: 1px solid rgba(0, 0, 0, 0.05);
	border-radius: 22px;
	backdrop-filter: blur(6px);
	-webkit-backdrop-filter: blur(6px);
	overflow: hidden;
}

.faq__shell h2 {
	margin: 0;
	padding: clamp(1.5rem, 3vw, 2.25rem);
	font-size: clamp(1.8rem, 2.6vw, 2.6rem);
	letter-spacing: -0.01em;
	color: #0d1117;
}

.faq__list {
	list-style: none;
	margin: 0;
	padding: 0 clamp(1.5rem, 3vw, 2.25rem) clamp(1.25rem, 2.5vw, 2rem);
	display: flex;
	flex-direction: column;
	gap: 0.5rem;
}

.faq__item {
	border-top: 1px solid rgba(0, 0, 0, 0.08);
}

.faq__item:first-of-type {
	border-top: 1px solid rgba(0, 0, 0, 0.08);
}

.faq__question {
	width: 100%;
	padding: 1rem 0;
	background: none;
	border: none;
	color: #0f172a;
	font-size: 1rem;
	font-weight: 700;
	text-align: left;
	display: flex;
	align-items: center;
	justify-content: space-between;
	gap: 1rem;
	cursor: pointer;
}

.faq__question:focus-visible {
	outline: 2px solid #0ea5e9;
	outline-offset: 4px;
	border-radius: 10px;
	padding: calc(1rem - 2px) 0;
	background: rgba(14, 165, 233, 0.06);
}

.faq__icon {
	position: relative;
	width: 18px;
	height: 18px;
	flex-shrink: 0;
}

.faq__icon::before,
.faq__icon::after {
	content: '';
	position: absolute;
	background: #0f172a;
	border-radius: 2px;
	transition: transform 0.2s ease;
}

.faq__icon::before {
	width: 18px;
	height: 2px;
	top: 8px;
	left: 0;
}

.faq__icon::after {
	width: 2px;
	height: 18px;
	top: 0;
	left: 8px;
}

.faq__icon--open::after {
	transform: scaleY(0);
}

.faq__answer {
	padding: 0 0 1.25rem 0;
	color: #1f2937;
	font-weight: 500;
	line-height: 1.55;
}

.accordion-enter-active,
.accordion-leave-active {
	transition: all 0.2s ease;
}

.accordion-enter-from,
.accordion-leave-to {
	opacity: 0;
	transform: translateY(-4px);
}

@media (max-width: 768px) {
	.faq {
		padding: 3rem 1rem;
	}

	.faq__shell h2 {
		padding: 1.5rem 1.25rem;
	}

	.faq__list {
		padding: 0 1.25rem 1.25rem;
	}

	.faq__question {
		font-size: 0.98rem;
		align-items: flex-start;
	}
}
</style>
