<!-- 
	@component
the about section of my page
src > lib > components > About.svelte
 -->

<!-- src/lib/components/About.svelte -->
<script context="module" lang="ts">
	export { default as About } from './About.svelte';
</script>

<script lang="ts">
	import Saos from 'saos';
	import { onMount } from 'svelte';
	import { fly } from 'svelte/transition';

	let isVisible = true;

	// Function to handle scroll event
	const handleScroll = () => {
		const aboutSection = document.getElementById('about');
		if (aboutSection) {
			const rect = aboutSection.getBoundingClientRect();
			isVisible = rect.top <= window.innerHeight;
		}
	};

	// Add scroll event listener
	onMount(() => {
		window.addEventListener('scroll', handleScroll);
		// Initial check on mount
		handleScroll();
		return () => {
			window.removeEventListener('scroll', handleScroll);
		};
	});
</script>

<div id="about" class="about-container">
	<div class="background-container absolute inset-0">
		<!-- Background image container -->
	</div>

	{#if isVisible}
		<div class="mx-[10rem] pt-[5rem]" transition:fly={{ y: 50, duration: 2000 }}>
			<p class="cool-font py-6">About me</p>
			<p class="text-black text-5xl cool-font">
				Hi i'm a NZSIA professional ski instructor. With over a decade of teaching experience. I prioritize in creating <span class="peg">personalized & engaging</span> lessons. Tailored to each individual needs,
				from beginners to the experienced.
			</p>
			I
		</div>
	{/if}
	<!-- {#if isVisible}
		<div
			transition:fly={{ y: 50, duration: 2000 }}
      class="about-content pt-10 mx-20 grid grid-cols-5 gap-4 absolute inset-0 text-center"
      >
			
			<div class="left-col col-span-3 flex flex-col justify-center items-center">
				
				<div class="header">
					<h1 class="text-black text-4xl nu-font mb-4">Your NZSIA Professional Ski Instructor</h1>
				</div>
			
				<div class="text">
					<p class="text-black text-lg px-5">
						With over a decade of immersive teaching experience spanning picturesque landscapes in
						New Zealand, the rugged terrains of the USA, the captivating snowscapes of Japan, and
						the enchanting slopes of Europe, I bring a wealth of expertise to the snowsport
						community. Throughout my journey, I've had the privilege of guiding and inspiring
						individuals of all ages, from enthusiastic beginners to seasoned adventurers, fostering
						a love for skiing that transcends skill levels. As a passionate instructor, I prioritize
						creating personalized and engaging lessons tailored to each individual's needs and
						aspirations. My commitment to excellence, paired with a friendly and caring approach,
						ensures that every learner feels empowered and confident on the slopes. Whether you're
						embarking on your first glide or seeking to refine your technique, I am dedicated to
						helping you reach your fullest potential and fostering a lifelong love for skiing
					</p>
				</div>
			</div>
			
			<div class="right-col col-span-2 flex justify-center items-center">
				<div class="item mb-20">
					<div class="polaroid">
						<img src="./nick5.JPG" alt="Nick Image" />
						<div class="nu-font text-black caption">Hi !</div>
					</div>
				</div>
			</div>
		</div>
	{/if} -->

	<section>
		<div class="w-full flex flex-col items-center pt-5">
			<h2 class="nu-font text-black text-4xl font-bold mb-4">Most popular Lessons 2024</h2>
			<div class="w-full max-w-screen-lg px-10 grid grid-cols-3 gap-4">
				<div class="col-span-1 !min-h-9 !rounded card card-hover text-center p-4">
					<h4 class="card-header">Private One-on-One</h4>
					<p />
				</div>

				<div class="col-span-1 !rounded card card-hover text-center p-4">
					<h4 class="card-header">Adult Group Lessons</h4>
					<p />
				</div>

				<div class="col-span-1 !rounded card card-hover text-center p-4">
					<h4 class="card-header">Childrens Group Lessons</h4>
					<p />
				</div>
			</div>
		</div>
	</section>
</div>

<style>

  /* .peg {
    background: hsla(194, 93%, 62%, 1);

background: linear-gradient(135deg, hsla(194, 93%, 62%, 1) 42%, hsla(202, 63%, 41%, 1) 64%);

background: -moz-linear-gradient(135deg, hsla(194, 93%, 62%, 1) 42%, hsla(202, 63%, 41%, 1) 64%);

background: -webkit-linear-gradient(135deg, hsla(194, 93%, 62%, 1) 42%, hsla(202, 63%, 41%, 1) 64%);
  } */

  /* .peg {
    color: hsla(194, 93%, 62%, 1);
    color: linear-gradient(135deg, hsla(194, 93%, 62%, 1) 42%, hsla(202, 63%, 41%, 1) 64%);
    color: -moz-linear-gradient(135deg, hsla(194, 93%, 62%, 1) 42%, hsla(202, 63%, 41%, 1) 64%);
    color: -webkit-linear-gradient(135deg, hsla(194, 93%, 62%, 1) 42%, hsla(202, 63%, 41%, 1) 64%);
  } */

  .peg {
    color: hsla(194, 55%, 49%, 1);
    color: linear-gradient(135deg, hsla(194, 55%, 49%, 1) 40%, hsla(202, 63%, 32%, 1) 64%);
    color: -moz-linear-gradient(135deg, hsla(194, 55%, 49%, 1) 40%, hsla(202, 63%, 32%, 1) 64%);
    color: -webkit-linear-gradient(135deg, hsla(194, 55%, 49%, 1) 40%, hsla(202, 63%, 32%, 1) 64%);
  }
	.glass {
		position: relative;
		background: inherit;
		overflow: hidden;
		border-radius: 16px;
		box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3), 0 6px 20px rgba(0, 0, 0, 0.15);
		z-index: 1;
	}

	.glass:before {
		content: '';
		position: absolute;
		background: inherit;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		margin: -20px;
		box-shadow: inset 0 0 500px rgba(255, 255, 255, 0.4);
		filter: blur(10px);
		z-index: -1;
	}

	.polaroid {
		background: #fff;
		padding: 1rem;
		box-shadow: 0 0.2rem 1.2rem rgba(0, 0, 0, 0.2);
	}
	.polaroid > img {
		max-width: 100%;
		height: auto;
		margin-bottom: 2rem;
	}
	.caption {
		font-size: 1.8rem;
		text-align: center;
		line-height: 2em;
		font-family: 'NeueMontreal-Regular', sans-serif;
	}
	.item {
		width: 100%;
		display: inline-block;
		margin-top: 2rem;
		filter: grayscale(100%);
	}
	.item .polaroid:before {
		content: '';
		position: absolute;
		z-index: -1;
		transition: all 0.35s;
	}
	.item:nth-of-type(4n + 1) {
		transform: scale(0.8, 0.8) rotate(5deg);
		transition: all 0.35s;
	}
	.item:nth-of-type(4n + 1) .polaroid:before {
		transform: rotate(6deg);
		height: 20%;
		width: 47%;
		bottom: 30px;
		right: 12px;
		box-shadow: 0 2.1rem 2rem rgba(0, 0, 0, 0.4);
	}
	.item:nth-of-type(4n + 2) {
		transform: scale(0.8, 0.8) rotate(-5deg);
		transition: all 0.35s;
	}
	.item:nth-of-type(4n + 2) .polaroid:before {
		transform: rotate(-6deg);
		height: 20%;
		width: 47%;
		bottom: 30px;
		left: 12px;
		box-shadow: 0 2.1rem 2rem rgba(0, 0, 0, 0.4);
	}
	.item:nth-of-type(4n + 4) {
		transform: scale(0.8, 0.8) rotate(3deg);
		transition: all 0.35s;
	}
	.item:nth-of-type(4n + 4) .polaroid:before {
		transform: rotate(4deg);
		height: 20%;
		width: 47%;
		bottom: 30px;
		right: 12px;
		box-shadow: 0 2.1rem 2rem rgba(0, 0, 0, 0.3);
	}
	.item:nth-of-type(4n + 3) {
		transform: scale(0.8, 0.8) rotate(-3deg);
		transition: all 0.35s;
	}
	.item:nth-of-type(4n + 3) .polaroid:before {
		transform: rotate(-4deg);
		height: 20%;
		width: 47%;
		bottom: 30px;
		left: 12px;
		box-shadow: 0 2.1rem 2rem rgba(0, 0, 0, 0.3);
	}
	.item:hover {
		filter: none;
		transform: scale(1, 1) rotate(0deg) !important;
		transition: all 0.35s;
	}
	.item:hover .polaroid:before {
		content: '';
		position: absolute;
		z-index: -1;
		transform: rotate(0deg);
		height: 90%;
		width: 90%;
		bottom: 0%;
		right: 5%;
		box-shadow: 0 1rem 3rem rgba(0, 0, 0, 0.2);
		transition: all 0.35s;
	}

	.about-container {
		height: 200vh;
		position: relative;
	}

	.background-container {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-image: url('/vertical-shot-mountains-bright-sky.jpg');
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		z-index: -1;
	}

	.about-content {
		position: relative;
		z-index: 1; /* Ensure content is above background */
	}

	@font-face {
		font-family: 'NeueMontreal-Regular';
		src: url('/NeueMontreal-Regular.otf') format('opentype');
		font-weight: normal;
		font-style: normal;
	}


  @font-face {
    font-family: 'ITC-Avant-Garde-Gothic-Bold';
    src: url('/ITC-Avant-Garde-Gothic-Bold.otf') format('opentype');
    font-weight: bold;
    font-style: normal;
  }

  .cool-font {
    font-family: 'ITC-Avant-Garde-Gothic-Bold', sans-serif;
    color: black;
  }

	.nu-font {
		font-family: 'NeueMontreal-Regular', sans-serif;
		/* font-family: 'NeueMontreal-Light', sans-serif; */
		color: black;
	}
</style>






