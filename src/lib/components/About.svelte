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
</script>

<div id="about" class="about-container">
  <div class="about">
      <div class="flex items-center justify-center">
          <Saos animation={'from-left 2s cubic-bezier(0.35, 0.5, 0.65, 0.95) both'}>
              <h2 class="text-black">About Us</h2>
              <p class="text-black">More info coming soon</p>
          </Saos>
      </div>
  </div>
</div>

<style>
    .about-container .about {
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: whitesmoke;
        opacity: 0;
        animation: -global-from-left 2s cubic-bezier(0.35, 0.5, 0.65, 0.95) both;
    }

    @keyframes -global-from-left {
        0% {
            transform: rotateX(50deg) translateX(-200vw) skewX(-50deg);
            opacity: 1;
        }
        100% {
            transform: rotateX(0deg) translateX(0) skewX(0deg);
            opacity: 1;
        }
    }
</style>



