<template>
	<section class="banner">
		<div class="banner__content">
			<h1>Transformez vos données en décisions.</h1>
			<button class="banner__cta">Tester la démo</button>
		</div>
	</section>
</template>

<style scoped>
.banner {
	position: relative;
	min-height: 360px;
	display: flex;
	align-items: center;
	justify-content: center;
	padding: 64px 24px;
	color: #ffffff;
	background: url('~/assets/img/banniere.png') center/cover no-repeat;
	text-align: center;
}

.banner__content {
	max-width: 960px;
	display: flex;
	flex-direction: column;
	gap: 24px;
}

.banner h1 {
	font-size: clamp(2rem, 3vw + 1rem, 3.5rem);
	font-weight: 700;
	line-height: 1.2;
	margin: 0;
}

.banner__cta {
	align-self: center;
	padding: 14px 28px;
	border: none;
	border-radius: 999px;
	background: #70ED70;
	color: #0b1c0f;
	font-size: 1rem;
	font-weight: 600;
	cursor: pointer;
	transition: transform 0.2s ease, background 0.2s ease;
}

.banner__cta:hover {
	background: #2ac042;
	transform: translateY(-2px);
}

.banner__cta:active {
	transform: translateY(0);
}

@media (max-width: 640px) {
	.banner {
		min-height: 320px;
		padding: 56px 16px;
	}

	.banner__content {
		gap: 16px;
	}
}
</style>
