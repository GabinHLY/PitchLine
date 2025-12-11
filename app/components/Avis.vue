<template>
	<section class="avis" aria-labelledby="avis-title">
		<div class="avis__shell">
			<figure class="avis__image" aria-hidden="true">
				<img :src="currentAvis.image" :alt="currentAvis.imageAlt" loading="lazy">
			</figure>

			<div class="avis__content" aria-live="polite">
				<h2 id="avis-title" class="avis__quote">{{ currentAvis.quote }}</h2>

				<div class="avis__author">
					<img class="avis__avatar" :src="currentAvis.avatar" :alt="`Portrait de ${currentAvis.name}`" loading="lazy">
					<div>
						<p class="avis__name">{{ currentAvis.name }}</p>
						<p class="avis__role">{{ currentAvis.role }}</p>
					</div>
				</div>

				<div class="avis__footer">
					<div v-if="hasMultiple" class="avis__dots" aria-label="Changer de témoignage">
						<button
							v-for="(item, idx) in avisList"
							:key="item.name + idx"
							type="button"
							class="avis__dot"
							:class="{ 'avis__dot--active': idx === activeIndex }"
							@click="goTo(idx)"
							:aria-label="`Voir le témoignage de ${item.name}`"
						/>
					</div>

					<div class="avis__controls" aria-hidden="true">
						<button
							type="button"
							class="avis__arrow"
							:class="{ 'is-disabled': !hasMultiple }"
							:disabled="!hasMultiple"
							@click="prev"
							aria-label="Témoignage précédent"
						>
							<span>&lsaquo;</span>
						</button>
						<button
							type="button"
							class="avis__arrow avis__arrow--active"
							:class="{ 'is-disabled': !hasMultiple }"
							:disabled="!hasMultiple"
							@click="next"
							aria-label="Témoignage suivant"
						>
							<span>&rsaquo;</span>
						</button>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<script setup>
import { computed, ref } from 'vue';
import avisHero from '@/assets/img/avis1.png';
import avatarPdp from '@/assets/img/pdp.png';

const avisList = [
	{
		quote: '“PitchLine a probablement été la chose la plus utile pour mon recrutement”',
		name: 'Julien Deprés',
		role: 'Joueur de U21',
		avatar: avatarPdp,
		image: avisHero,
		imageAlt: 'Joueur de football assis sur un banc',
	},
	{
		quote: '“En un clic, j’ai des séquences claires pour briefer le staff et les joueurs.”',
		name: 'Claire Martin',
		role: 'Analyste vidéo N2',
		avatar: avatarPdp,
		image: avisHero,
		imageAlt: 'Analyse vidéo depuis le banc',
	},
	{
		quote: '“Les données sont enfin lisibles et utilisables dès le lendemain du match.”',
		name: 'Marc Leroy',
		role: 'Entraîneur U19',
		avatar: avatarPdp,
		image: avisHero,
		imageAlt: 'Staff technique au bord du terrain',
	},
];

const activeIndex = ref(0);
const total = computed(() => avisList.length);
const hasMultiple = computed(() => total.value > 1);

const currentAvis = computed(() => avisList[activeIndex.value]);

const next = () => {
	if (!hasMultiple.value) return;
	activeIndex.value = (activeIndex.value + 1) % total.value;
};

const prev = () => {
	if (!hasMultiple.value) return;
	activeIndex.value = (activeIndex.value - 1 + total.value) % total.value;
};

const goTo = (index) => {
	if (!hasMultiple.value) return;
	activeIndex.value = index;
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rethink+Sans:ital,wght@0,400;0,600;0,700;1,700&display=swap');

.avis {
	padding: clamp(3rem, 5vw, 5rem) clamp(1.25rem, 4vw, 3rem);
	background: #ffffff;
	color: #0c0c12;
	font-family: 'Rethink Sans', system-ui, -apple-system, sans-serif;
}

.avis__shell {
	max-width: 1400px;
	margin: 0 auto;
	display: grid;
	grid-template-columns: minmax(320px, 0.9fr) minmax(320px, 1fr);
	gap: clamp(2rem, 4vw, 3rem);
	align-items: center;
}

.avis__image {
	margin: 0;
	border-radius: 22px;
	overflow: hidden;
	box-shadow: 0 24px 60px rgba(12, 12, 18, 0.12);
}

.avis__image img {
	display: block;
	width: 100%;
	height: 100%;
	object-fit: cover;
}

.avis__content {
	display: grid;
	gap: clamp(1.5rem, 3vw, 2.5rem);
	align-content: center;
}

.avis__footer {
	display: flex;
	align-items: center;
	justify-content: space-between;
	gap: 1rem;
	flex-wrap: wrap;
}

.avis__dots {
	display: inline-flex;
	align-items: center;
	gap: 0.5rem;
}

.avis__dot {
	width: 10px;
	height: 10px;
	border-radius: 50%;
	border: 1px solid #d1d5db;
	background: #ffffff;
	cursor: pointer;
	transition: all 0.2s ease;
}

.avis__dot--active {
	background: #0c0c12;
	border-color: #0c0c12;
}

.avis__quote {
	margin: 0;
	font-size: clamp(2rem, 3vw, 2.75rem);
	line-height: 1.05;
	font-weight: 700;
	font-style: italic;
	letter-spacing: -0.01em;
}

.avis__author {
	display: inline-flex;
	align-items: center;
	gap: 0.75rem;
}

.avis__avatar {
	width: 60px;
	height: 60px;
	border-radius: 50%;
	object-fit: cover;
	flex-shrink: 0;
}

.avis__name {
	margin: 0 0 0.15rem;
	font-weight: 700;
	font-size: 1rem;
}

.avis__role {
	margin: 0;
	color: #4b5563;
	font-size: 0.95rem;
}

.avis__controls {
	margin-top: auto;
	display: flex;
	justify-content: flex-end;
	gap: 0.75rem;
}

.avis__arrow {
	width: 42px;
	height: 42px;
	border-radius: 50%;
	border: 1px solid #d1d5db;
	background: #ffffff;
	color: #6b7280;
	font-size: 1.4rem;
	line-height: 1;
	display: inline-flex;
	align-items: center;
	justify-content: center;
	cursor: pointer;
	transition: all 0.2s ease;
}

.avis__arrow:hover {
	border-color: #0c0c12;
	color: #0c0c12;
	transform: translateY(-1px);
}

.avis__arrow.is-disabled {
	opacity: 0.4;
	border-color: #d1d5db;
	color: #9ca3af;
	cursor: not-allowed;
	transform: none;
}

.avis__arrow--active {
	border-color: #0c0c12;
	color: #0c0c12;
}

@media (max-width: 1024px) {
	.avis__shell {
		grid-template-columns: 1fr;
	}

	.avis__controls {
		justify-content: flex-start;
	}
}

@media (max-width: 640px) {
	.avis {
		padding: 2.5rem 1.25rem;
	}

	.avis__quote {
		font-size: clamp(1.6rem, 6vw, 2.1rem);
	}

	.avis__avatar {
		width: 50px;
		height: 50px;
	}
}
</style>
