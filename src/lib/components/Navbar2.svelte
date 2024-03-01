

<script context="module" lang="ts">
	export { default as Navbar2 } from './Navbar2.svelte';
</script>

<script lang="ts">
	import { onMount } from 'svelte';
	import { navLinks } from '$lib/components/navigation';

	let active = '';
	let scrolled = false;
	let isDropdownOpen = false;

	onMount(() => {
		const handleScroll = () => {
			const scrollTop = window.scrollY;
			scrolled = scrollTop > 100;
		};

		window.addEventListener('scroll', handleScroll);

		return () => window.removeEventListener('scroll', handleScroll);
	});

	onMount(() => {
		window.addEventListener('click', (event) => {
			const target = event.target as HTMLElement;
			if (!target.closest('#langDropdown')) {
				isDropdownOpen = false;
			}
		});
	});

	function toggleDropdown() {
		isDropdownOpen = !isDropdownOpen;
	}
</script>

<nav class="paddingX w-full flex items-center justify-between py-5 px-4 fixed top-0 z-20 bg-transparent">
  <!-- Left side content -->
  <div class="flex items-center">
      <a href="/" class="flex items-center gap-2" on:click={() => { active = ''; window.scrollTo(0, 0); }}>
          <div class="h-[1.7rem] w-[18.2rem] flex items-center">
              <h1 class="nu-font text-3xl">
                  <span>Nicholas</span>
                  <span class="bellion-font text-3xl">Bellion</span>
              </h1>
          </div>
      </a>
  </div>

  <!-- Right side content -->
  <div class="flex items-center gap-6">
      <ul class="list-none flex gap-6 items-center">
          {#each navLinks as nav (nav.id)}
              <li class="{`${
                  active === nav.title ? '!text-blue ' : 'text-secondary'
              } hover:text-blue text-[18px] font-medium cursor-pointer`}">
                  <a class="cursor-pointer text-white nu-font font-bold inverted-2 py-1 px-4"
                      href={`#${nav.id}`}>{nav.title}</a>
              </li>
          {/each}
      </ul>

      <div class="relative inline-block text-left">
          <div>
              <button on:click={toggleDropdown} type="button"
                  class="text-white nu-font font-bold inverted-2 py-1 px-4" id="langDropdown">
                  Language
                  <svg class="w-5 h-5 inline-block ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"
                      xmlns="http://www.w3.org/2000/svg">
                      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                  </svg>
              </button>
          </div>
          {#if isDropdownOpen}
              <div class="origin-top-right absolute right-0 mt-2 w-40 rounded-md shadow-lg" id="langDropdownContent">
                  <div class="py-1">
                      <a href="#"
                          class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900">English</a>
                      <a href="#"
                          class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900">Japanese</a>
                  </div>
              </div>
          {/if}
      </div>
  </div>
</nav>

<style>
  .navbar {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem;
      max-height: 5rem;
      z-index: 1000;
  }

  .nu-font {
      font-family: 'NeueMontreal-Regular', sans-serif;
      color: black;
  }

  .bellion-font {
      font-family: 'HagluetaKlaristtoSerif', serif;
      color: black;
  }

  .inverted-2 {
      background: linear-gradient(90deg, #000 50%, #fff 0), linear-gradient(-90deg, #000 50%, #fff 0),
          linear-gradient(90deg, #0000 50%, #000 0), linear-gradient(-90deg, #0000 50%, #000 0);
      background-repeat: no-repeat;
      background-size: 200% 51%;
      background-position: top left, bottom right;
      -webkit-background-clip: text, text, padding-box, padding-box;
      background-clip: text, text, padding-box, padding-box;
      transition: 0.8s;
  }

  .inverted-2:hover {
      background-position: top right, bottom left;
      color: whitesmoke;
  }
</style>
