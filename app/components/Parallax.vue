<script setup lang="ts">
import { onMounted, onBeforeUnmount, ref, nextTick } from 'vue';
import frame20 from '~/assets/img/Frame 20.png';

interface Step {
  num: string;
  title: string;
  body: string;
}

const steps: Step[] = [
  {
    num: '01',
    title: 'Déposez la vidéo',
    body: "Ajoutez votre match et laissez l’outil préparer la timeline."
  },
  {
    num: '02',
    title: 'Tagguez les actions',
    body: 'Marquez tirs, récupérations, pertes, zones clés en quelques clics.'
  },
  {
    num: '03',
    title: 'Lisez les insights',
    body: 'Visualisez cartes de chaleur, séquences fortes et stats par joueur.'
  }
];

const activeStep = ref(0);

// les éléments qui servent de “trigger” au scroll (wrappers des images)
const stepEls = ref<HTMLElement[]>([]);
const setStepRef = (el: HTMLElement | null, index: number) => {
  if (!el) return;
  stepEls.value[index] = el;
};

let observer: IntersectionObserver | null = null;

onMounted(async () => {
  await nextTick(); // on est sûr que le DOM est là

  const visibleIndices = new Set<number>();

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        const idx = Number((entry.target as HTMLElement).dataset.stepIndex);
        if (entry.isIntersecting) {
          visibleIndices.add(idx);
        } else {
          visibleIndices.delete(idx);
        }
      });

      if (!visibleIndices.size) return;

      const viewportCenter = window.innerHeight / 2;
      let bestIdx = activeStep.value;
      let bestDistance = Infinity;

      visibleIndices.forEach((idx) => {
        const el = stepEls.value[idx];
        if (!el) return;

        const rect = el.getBoundingClientRect();
        const center = rect.top + rect.height / 2;
        const distance = Math.abs(center - viewportCenter);

        if (distance < bestDistance) {
          bestDistance = distance;
          bestIdx = idx;
        }
      });

      activeStep.value = bestIdx;
    },
    {
      threshold: 0.3,
      root: null
    }
  );

  stepEls.value.forEach((el) => {
    if (el) observer?.observe(el);
  });
});

onBeforeUnmount(() => {
  if (observer) {
    observer.disconnect();
    observer = null;
  }
});
</script>

<template>
  <section class="parallax">
    <div class="parallax__body">
      <!-- Colonne gauche sticky -->
      <div class="parallax__left">
        <div class="parallax__title">
          <h2>Comment se déroule une analyse de match&nbsp;?</h2>
        </div>

        <div class="parallax__numbers">
          <div class="parallax__step">
            <transition name="slide-num" mode="out-in">
              <span
                :key="steps[activeStep].num"
                class="parallax__num"
              >
                {{ steps[activeStep].num }}
              </span>
            </transition>

            <div class="parallax__text">
              <transition name="fade-slide" mode="out-in">
                <h3 :key="steps[activeStep].title">
                  {{ steps[activeStep].title }}
                </h3>
              </transition>

              <transition name="fade-slide" mode="out-in">
                <p :key="steps[activeStep].body">
                  {{ steps[activeStep].body }}
                </p>
              </transition>
            </div>
          </div>
        </div>
      </div>

      <!-- Colonne droite avec les images -->
      <div class="parallax__images">
        <div
          v-for="(step, index) in steps"
          :key="step.num"
          :data-step-index="index"
          :ref="(el) => setStepRef(el as HTMLElement | null, index)"
          class="parallax__image-wrapper"
          :class="{ 'parallax__image-wrapper--active': index === activeStep }"
        >
          <img
            :src="frame20"
            :alt="`Étape ${step.num}`"
            class="parallax__image"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.parallax {
  max-width: 1400px;
  margin: 0 auto;
  padding: 8rem 1.25rem;
  --image-height: 500px;
}

.parallax__body {
  display: grid;
  grid-template-columns: 1fr 1.3fr;
  gap: 48px;
  align-items: flex-start;
}


.parallax__left {
  position: sticky;
  top: 96px;              
  display: flex;
  flex-direction: column;
}

.parallax__title {
  color: #101010;
  margin-bottom: 32px;
}

.parallax__title h2 {
  font-size: 32px;
  font-weight: 700;
  line-height: 1.25;
}

.parallax__numbers {
  margin-top: 0;
  padding-bottom: 0;
}

.parallax__step {
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.parallax__num {
  font-size: 160px;
  font-weight: 800;
  line-height: 1;
  letter-spacing: 0.08em;
  background: #000;
  -webkit-background-clip: text;
  color: transparent;
}

.parallax__text {
  display: grid;
  gap: 6px;
  max-width: 360px;
}

.parallax__text h3 {
  margin: 0;
  font-size: 20px;
  font-weight: 700;
  color: #0f172a;
}

.parallax__text p {
  margin: 0;
  font-size: 15px;
  line-height: 1.5;
  color: #374151;
}

/* Colonne droite */
.parallax__images {
  display: flex;
  flex-direction: column;
  gap: 32px;
  padding: 4rem 0;
}

.parallax__image-wrapper {
  width: 100%;
  height: var(--image-height);
  border-radius: 24px;
  overflow: hidden;
  transform: scale(0.94);
  opacity: 0.4;
  transition:
    transform 240ms ease,
    opacity 240ms ease,
    box-shadow 240ms ease;
}

.parallax__image-wrapper--active {
  transform: scale(1);
  opacity: 1;
}

.parallax__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}

/* Animations texte/numéro */
.slide-num-enter-active,
.slide-num-leave-active {
  transition: transform 220ms ease, opacity 220ms ease;
}

.slide-num-enter-from {
  transform: translateY(80%);
  opacity: 0;
}

.slide-num-leave-to {
  transform: translateY(-80%);
  opacity: 0;
}

.fade-slide-enter-active,
.fade-slide-leave-active {
  transition: transform 200ms ease, opacity 200ms ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
  transform: translateY(12px);
  opacity: 0;
}

/* Responsive */
@media (max-width: 900px) {
  .parallax {
    --image-height: 300px;
    padding: 4rem 1.25rem;
  }

  .parallax__body {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  /* On désactive le sticky sur mobile */
  .parallax__left {
    position: static;
  }

  .parallax__num {
    font-size: 100px;
  }

  .parallax__images {
    padding: 0;
    gap: 24px;
  }
}

@media (max-width: 600px) {
  .parallax__title h2 {
    font-size: 24px;
  }
  
  .parallax__num {
    font-size: 80px;
  }
  
  .parallax {
    --image-height: 220px;
  }
}
</style>
