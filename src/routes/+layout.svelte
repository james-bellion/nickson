<script lang="ts">
	import '../app.postcss';
import About from '$lib/components/About.svelte';
import Contact from '$lib/components/Contact.svelte';
import Hero from '$lib/components/Hero.svelte';
import Navbar from '$lib/components/Navbar.svelte';
  
	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { AppShell, storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });
</script>
<AppShell>
  <div slot="pageHeader">
  </div>

  <main class="!overflow-hidden">
    <Hero />
    <About />
    <slot />
    <Contact />
  </main>

  <div slot="pageFooter">Page Footer</div>
</AppShell>

 

<style>
 body {
  /* background-image: url('/nickblue1.JPG'); */
  /* background-size: cover; 
    background-position: center center; 
    background-repeat: no-repeat; 
    width: 100%;
    height: 100vh; 
    z-index: -1; */
 }
</style>