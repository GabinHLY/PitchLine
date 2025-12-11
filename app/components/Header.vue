
<template>
	<header class="hero-header">
		<div class="nav-shell" :class="{ 'nav-shell--open': isMenuOpen }">
			<div class="nav-main">
				<NuxtLink to="/" class="brand" aria-label="Pitchline home" @click="isMenuOpen = false">
					<img src="../assets/img/Logo.svg" alt="Pitchline">
				</NuxtLink>

				<div class="mobile-controls">
					<NuxtLink to="/demo" class="cta cta--mobile">Démo</NuxtLink>
					<button 
						class="menu-toggle" 
						@click="isMenuOpen = !isMenuOpen" 
						:aria-expanded="isMenuOpen"
						aria-label="Menu"
					>
						<span class="hamburger-line"></span>
						<span class="hamburger-line"></span>
					</button>
				</div>
			</div>

			<nav class="links" :class="{ 'links--open': isMenuOpen }" aria-label="Navigation principale">
				<NuxtLink to="/demo" class="cta cta--desktop">Tester la démo</NuxtLink>
			</nav>
		</div>
	</header>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isMenuOpen = ref(false);
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Rethink+Sans:ital,wght@0,400..800;1,400..800&display=swap');

.hero-header {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	z-index: 30;
	padding: 2rem 1.5rem;
	display: flex;
	justify-content: center;
}

.nav-shell {
	width: min(1250px, 100%);
	background: rgba(240, 241, 241, 0.65);
	backdrop-filter: blur(12px);
	-webkit-backdrop-filter: blur(12px);
	border: 1px solid rgba(255, 255, 255, 0.4);
	border-radius: 999px;
	padding: 0.65rem 0.75rem 0.65rem 1.5rem;
	display: flex;
	align-items: center;
	justify-content: space-between;
	font-family: 'Rethink Sans', sans-serif;
	transition: all 0.3s ease;
}

.nav-main {
	display: contents;
}

.brand {
	display: flex;
	align-items: center;
	text-decoration: none;
	margin-right: auto;
}

.brand img {
	height: 24px;
	width: auto;
}

.links {
	display: flex;
	align-items: center;
	gap: 2rem;
	margin-left: auto;
}

.link {
	color: #1f2937;
	text-decoration: none;
	font-weight: 500;
	font-size: 0.95rem;
	transition: color 0.2s ease;
}

.link:hover {
	color: #0ea5e9;
}

.cta {
	display: inline-flex;
	align-items: center;
	justify-content: center;
	padding: 0.6rem 1.4rem;
	border-radius: 999px;
	background: #70ED70;
	color: #0f172a;
	font-weight: 700;
	font-size: 0.95rem;
	text-decoration: none;
	transition: transform 0.2s ease;
}

.cta:hover {
	transform: translateY(-1px);
}

.cta--mobile {
	display: none;
}

.mobile-controls {
	display: none;
}

.menu-toggle {
	display: none;
	background: none;
	border: none;
	cursor: pointer;
	padding: 0.5rem;
	flex-direction: column;
	gap: 5px;
	justify-content: center;
	align-items: center;
	width: 40px;
	height: 40px;
	border-radius: 50%;
	background: rgba(255, 255, 255, 0.5);
}

.hamburger-line {
	width: 20px;
	height: 2px;
	background-color: #1f2937;
	border-radius: 2px;
	transition: all 0.3s ease;
}

/* Responsive */
@media (max-width: 900px) {
	.hero-header {
		padding: 1rem;
	}

	.nav-shell {
		flex-direction: column;
		align-items: stretch;
		padding: 0.75rem 1rem;
		border-radius: 24px;
		gap: 0;
		overflow: hidden;
	}

	.nav-main {
		display: flex;
		align-items: center;
		justify-content: space-between;
		width: 100%;
	}

	.mobile-controls {
		display: flex;
		align-items: center;
		gap: 0.75rem;
	}

	.menu-toggle {
		display: flex;
	}

	.cta--desktop {
		display: none;
	}

	.cta--mobile {
		display: inline-flex;
		padding: 0.5rem 1rem;
		font-size: 0.9rem;
	}

	.links {
		display: none;
		flex-direction: column;
		width: 100%;
		gap: 0;
		margin: 0;
		padding-top: 0;
		opacity: 0;
		transform: translateY(-10px);
		transition: all 0.3s ease;
	}

	/* Open State */
	.nav-shell--open {
		background: rgba(240, 241, 241, 0.95);
		border-radius: 24px;
		gap: 1.5rem;
		padding-bottom: 1.5rem;
	}

	.links--open {
		display: flex;
		opacity: 1;
		transform: translateY(0);
		padding-top: 1rem;
		border-top: 1px solid rgba(0,0,0,0.05);
	}

	.links--open .link {
		width: 100%;
		padding: 0.75rem 0;
		text-align: center;
		font-size: 1.1rem;
	}

	/* Hamburger Animation */
	.nav-shell--open .hamburger-line:first-child {
		transform: translateY(3.5px) rotate(45deg);
	}

	.nav-shell--open .hamburger-line:last-child {
		transform: translateY(-3.5px) rotate(-45deg);
	}
}
</style>
