<template>
  <div class="cards-container">
    <div class="card" v-for="n in 3" :key="n">
      <img src="~/assets/img/Frame 21.png" alt="Card Image" />
    </div>
  </div>
</template>

<style scoped>
.cards-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 2rem 1.25rem 8rem;
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 24px;
}

@media (min-width: 768px) {
  .cards-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .cards-container {
    grid-template-columns: repeat(3, 1fr);
  }
}

.card {
  width: 100%;
  height: auto;
  aspect-ratio: 3/4;
  border-radius: 16px;
  overflow: hidden;
  transition: transform 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
}

.card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
</style>
