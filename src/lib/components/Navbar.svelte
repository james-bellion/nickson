<!-- 
	@component
Nav bar
src > lib > Navbar.svelte
TODO: add to top of the page and when i scroll down I want it to stay at the top of my viewport so i can click and navigate to each section
 -->
<script context="module" lang="ts">
  export { default as Navbar } from './Navbar.svelte';
</script>

<script lang="ts">
  import { onMount } from 'svelte';

  let src = '/logo-no-background.png';
  let isDropdownOpen = false;

  onMount(() => {
    // Close the dropdown if the user clicks outside of it
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


<div class="navbar flex w-full">
  <div class="h-[1.7rem] w-[18.2rem] flex items-center">
    <h1 class="nu-font text-3xl">
      <span>Nicholas</span>
      <span class="bellion-font text-3xl">Bellion</span>
    </h1>
  </div>
  <div class="flex justify-end items-center">
    <nav class="flex space-x-4 pr-10 list-none font-semibold text-xl gap-3">
      <li><a href="#" class="text-white nu-font font-bold inverted-2 py-1 px-4">Home</a></li>
      <li><a href="#" class="text-white nu-font font-bold inverted-2 py-1 px-4">About</a></li>
      <li><a href="#" class="text-white nu-font font-bold inverted-2 py-1 px-4">Contact</a></li>
      <div class="relative inline-block text-left">
        <div>
          <button on:click={toggleDropdown} type="button" class="text-white nu-font font-bold inverted-2 py-1 px-4" id="langDropdown">
            Language
            <svg class="w-5 h-5 inline-block ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M19 9l-7 7-7-7"></path>
            </svg>
          </button>
        </div>
        {#if isDropdownOpen}
          <div class="origin-top-right absolute right-0 mt-2 w-40 rounded-md shadow-lg" id="langDropdownContent">
            <div class="py-1">
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900">English</a>
              <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900">Japanese</a>
            </div>
          </div>
        {/if}
      </div>
    </nav>
  </div>
</div>

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
    /* background-color: transparent;
    background-color: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(5px); */
    max-height: 5rem;
    z-index: 1000; /* Set a high z-index to ensure it appears above other elements */
  }

  /* gg */
  @font-face {
    font-family: 'NeueMontreal-Regular';
    src: url('/NeueMontreal-Regular.otf') format('opentype');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'NeueMontreal-Light';
    src: url('/NeueMontreal-Light.otf') format('opentype');
    font-weight: normal;
    font-style: normal;
  }

  /* gg */
  .nu-font {
    font-family: 'NeueMontreal-Regular', sans-serif; 
    /* font-family: 'NeueMontreal-Light', sans-serif; */
    color: black;
  }

  @font-face {
    font-family: 'CormorantGaramond-Regular';
    src: url('/CormorantGaramond-Regular.ttf') format('truetype'); /* Correct path to the font file */
    font-weight: normal;
    font-style: normal;
  }

  .bellion-font {
    /* font-family: 'CormorantGaramond-Regular', serif; */
    /* font-family: 'Calture-Rowasn Serif', sans-serif; */
    /* gg ok */
    /* font-family: 'Quattrocento-Regular', serif; */
    
    /* og */
    font-family: 'HagluetaKlaristtoSerif', serif;
    color: black;
  }

  @font-face {
    font-family: 'Calture-Rowasn Serif';
    src: url('/Calture-Rowasn Serif.otf') format('opentype');
    font-weight: normal;
    font-style: normal;
  }

  @font-face {
    font-family: 'Quattrocento-Regular';
    src: url('/Quattrocento-Regular.ttf') format('truetype'); /* Correct path to the font file */
    font-weight: normal;
    font-style: normal;
  }

  /* .custom-font {
    font-family: 'CormorantGaramond-Regular', sans-serif;
  } */

  @font-face {
    font-family: 'HagluetaKlaristtoSerif';
    src: url('/HagluetaKlaristtoSerif.otf') format('opentype');
    font-weight: normal;
    font-style: normal;
  }



.inverted-2 {
  background:
    linear-gradient( 90deg, #000  50%, #fff 0),
    linear-gradient(-90deg, #000  50%, #fff 0),
    linear-gradient( 90deg, #0000 50%, #000 0),
    linear-gradient(-90deg, #0000 50%, #000 0);
  background-repeat: no-repeat;
  background-size: 200% 51%;
  background-position: top left, bottom right;
  -webkit-background-clip: text, text, padding-box, padding-box;
          background-clip: text, text, padding-box, padding-box;
  transition: 0.8s
}

.inverted-2:hover {
  background-position: top right, bottom left;
  color: whitesmoke;
  list-style-type: none;
}

</style>
