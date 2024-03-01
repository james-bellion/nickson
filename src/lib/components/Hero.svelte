<!-- 
	@component
the hero section of my page
src > lib > components > Hero.svelte
 -->

<script context="module" lang="ts">
	export { default as Hero } from './Hero.svelte';
</script>

<script lang="ts">
	// Hero component logic if needed

	import Navbar from './Navbar.svelte';
	import Navbar2 from './Navbar2.svelte';

	('$lib/components/Navbar2.svelte');
	import { routes } from '$lib/components/navigation';
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';

	let isVisible = true;

	// Function to handle scroll event
	const handleScroll = () => {
		isVisible = window.scrollY === 0;
	};

	// Add scroll event listener
	onMount(() => {
		window.addEventListener('scroll', handleScroll);
		return () => {
			window.removeEventListener('scroll', handleScroll);
		};
	});
</script>

<!-- Add more snowflakes with different durations and delays -->
<div class="snowflake" style="left: 10%; animation-duration: 10s; animation-delay: 1s;" />
<div class="snowflake" style="left: 20%; animation-duration: 8s; animation-delay: 2s;" />
<div class="snowflake" style="left: 30%; animation-duration: 12s; animation-delay: 0s;" />
<div class="snowflake" style="left: 40%; animation-duration: 15s; animation-delay: 1s;" />
<div class="snowflake" style="left: 50%; animation-duration: 9s; animation-delay: 2s;" />
<!-- Add more snowflakes -->
<div class="snowflake" style="left: 60%; animation-duration: 11s; animation-delay: 0s;" />
<div class="snowflake" style="left: 70%; animation-duration: 14s; animation-delay: 1s;" />
<div class="snowflake" style="left: 80%; animation-duration: 10s; animation-delay: 2s;" />

<div id="home" class="hero flex flex-col justify-center items-center">
	<!-- <Navbar /> -->
	<Navbar2 />
	<!-- <Navbar /> -->

	<!-- main text nd call to action button -->
	{#if isVisible}
		<div
			class="text-container flex flex-col items-center justify-center"
			transition:fade={{ duration: 500 }}
		>
			<!-- <h2 class="custom-font text-3xl text-black">Nick Bellion</h2> -->
			<h2 class="nu-font text-black relative bottom-7 text-lg">
				private instructor, new zealand & japan
			</h2>
			<h2 class="HerovaitalicOblique text-6xl text-black relative bottom-4">
				Carve confidence, reach peaks.
			</h2>
			<!-- <h2 class="NeueMontreal-Regular text-6xl text-black relative bottom-1">New Zealand</h2> -->
		</div>
		<div transition:fade={{ duration: 500 }}>
			<button
				class="border border-white rounded-3xl background text-white px-4 py-2 m-2 transition-all duration-300 hover:bg-white hover:text-black hover:shadow-lg transform hover:scale-105 focus:outline-none focus:shadow-outline"
			>
				<a href={routes.CONTACT}>Book Now</a>
			</button>

			<button
				class="border glass bg-black border-white rounded-3xl text-white px-4 py-2 m-2 transition-all duration-300 hover:bg-white hover:text-black hover:shadow-lg transform hover:scale-105 focus:outline-none focus:shadow-outline"
			>
				<a href={routes.ABOUT}>My Story</a>
			</button>
		</div>
	{/if}

	<div transition:fade={{ duration: 500 }} class="absolute xs:bottom-10 bottom-5 w-full flex justify-center items-center">
		{#if isVisible}
    <svg
			width="30px"
			height="100%"
			viewBox="0 0 247 390"
			version="1.1"
			xmlns="http://www.w3.org/2000/svg"
			xmlns:xlink="http://www.w3.org/1999/xlink"
			style="fill-rule:evenodd;clip-rule:evenodd;stroke-linecap:round;stroke-linejoin:round;stroke-miterlimit:1.5;"
		>
			<path
				id="wheel"
				d="M123.359,79.775l0,72.843"
				style="fill:none;stroke:#fff;stroke-width:20px;"
			/>
			<path
				id="mouse"
				d="M236.717,123.359c0,-62.565 -50.794,-113.359 -113.358,-113.359c-62.565,0 -113.359,50.794 -113.359,113.359l0,143.237c0,62.565 50.794,113.359 113.359,113.359c62.564,0 113.358,-50.794 113.358,-113.359l0,-143.237Z"
				style="fill:none;stroke:#fff;stroke-width:20px;"
			/>
		</svg>
    {/if}
	</div>
</div>

<style>
.background {
background: hsla(243, 57%, 53%, 1);

background: linear-gradient(135deg, hsla(243, 57%, 53%, 1) 12%, hsla(319, 55%, 46%, 1) 100%);

background: -moz-linear-gradient(135deg, hsla(243, 57%, 53%, 1) 12%, hsla(319, 55%, 46%, 1) 100%);

background: -webkit-linear-gradient(135deg, hsla(243, 57%, 53%, 1) 12%, hsla(319, 55%, 46%, 1) 100%);


}

	.hero {
		height: 100vh;
		display: flex;
		/* justify-content: center;
    align-items: center; */
		/* background-image: url('/nickblue1.JPG');  */
		/* background-image: url('https://images4.alphacoders.com/108/108818.jpg');  */
		/* background-image: url('/skiwallp2.jpg');good*/
		background-image: url('/skiEdit.png');

		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		color: white;
		top: 50;
	}

	.hero::after {
		content: '';
		position: absolute;
		left: 0;
		bottom: 0;
		width: 100%;
		height: 30%;
		background: linear-gradient(to bottom, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.8));
		pointer-events: none;
	}

	@font-face {
		font-family: 'Calture-Rowasn Serif';
		src: url('/Calture-Rowasn Serif.otf') format('opentype');
		font-weight: normal;
		font-style: normal;
	}

	.custom-font {
		font-family: 'Calture-Rowasn Serif', sans-serif;
	}

	@font-face {
		font-family: 'NeueMontreal-Regular';
		src: url('/NeueMontreal-Regular.otf') format('opentype');
		font-weight: normal;
		font-style: normal;
	}

	.nu-font {
		font-family: 'NeueMontreal-Regular', sans-serif;
		/* font-family: 'NeueMontreal-Light', sans-serif; */
		color: black;
	}

	@font-face {
		font-family: 'Sdasian-WyDon';
		src: url('/Sdasian-WyDon.ttf') format('truetype');
		font-weight: normal;
		font-style: normal;
	}

	.bento {
		font-family: 'Sdasian-WyDon', sans-serif;
	}

	@font-face {
		font-family: 'HerovaitalicOblique';
		src: url('/HerovaitalicOblique-z8YoL.otf') format('opentype');
		font-weight: normal;
		font-style: normal;
	}

	.HerovaitalicOblique {
		font-family: 'HerovaitalicOblique', sans-serif;
		/* Additional styles for the 'hero-font' class if needed */
	}

	/************************************************************/
	.snowfall {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		pointer-events: none;
	}

	.snowflake {
		position: absolute;
		background-color: #fff;
		width: 5px;
		height: 5px;
		border-radius: 50%;
		animation: snowfall linear infinite;
		pointer-events: none;
		opacity: 1;
	}

	@keyframes snowfall {
		0% {
			transform: translateY(0) translateX(0) rotate(0deg);
			opacity: 1;
		}
		50% {
			transform: translateY(100vh) translateX(10%) rotate(360deg);
			opacity: 0.5;
		}
		100% {
			transform: translateY(200vh) translateX(20%) rotate(720deg);
			opacity: 0;
		}
	}

	/**************************************************/
	blue-g {
		background-color: #50d8d7;
		background-image: linear-gradient(316deg, #50d8d7 0%, #923993 74%);
	}

	@keyframes scroll {
		0% {
			transform: translateY(0);
		}
		30% {
			transform: translateY(60px);
		}
	}

	svg #wheel {
		animation: scroll ease 2s infinite;
	}
</style>
