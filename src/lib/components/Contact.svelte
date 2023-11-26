<!-- 
	@component
the contact section of my page
src > lib > components > Contact.svelte
 -->
 <script context="module" lang="ts">
  export { default as Contact } from './Contact.svelte';
</script>

<script lang="ts">
  // Contact component logic if needed
</script>

<div id="contact" class="contact hidden">
  <h2>Contact Us</h2>
  <p>Your Contact Section Content</p>
</div>

<style>
  .contact {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #4caf50;
    color: white;
  }
</style>
