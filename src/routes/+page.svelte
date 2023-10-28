<script>

	import { AppShell } from "@skeletonlabs/skeleton";

</script>


<AppShell>
	<svelte:fragment slot="header"><img src="Public/Images/logo-no-background.png" alt="Logo"/></svelte:fragment>
	<!-- (sidebarRight) -->
	<!-- (pageHeader) -->
	<!-- Router Slot -->
	<slot />
	<!-- ---- / ---- -->
	<svelte:fragment slot="pageFooter">Page Footer</svelte:fragment>
	<!-- (footer) -->
</AppShell>
