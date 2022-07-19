
<script lang="ts">
	import { LandingPage } from './the-content/content';
	import '../app.sass';
	import DeskNav from '$lib/desk-nav.svelte';
	import MobileNav from '$lib/mobile/mobile-nav.svelte';
	import MediaQuery from '$lib/media-query.svelte';
	import Footer from '$lib/footer.svelte';
</script>

<MediaQuery query="(min-width: 850px)" let:matches>
	{#if matches}
		<DeskNav />
	{/if}
</MediaQuery>

<MediaQuery query="(max-width: 850px)" let:matches>
	{#if matches}
		<MobileNav />
	{/if}
</MediaQuery>

<main>
	<slot />
</main>

<Footer footerData={LandingPage.footer} />