<script context="module">
	export const load = async ({ url, fetch }) => {
		const res = await fetch(`../../post/landing-page.json`);

		if (res.status === 404) {
			const error = new Error(`Footer Unavailable.`);
			return { status: 404, error };
		} else {
			const ftdata = await res.json();
			
			return {
				props: {
					ftdata
				}
			};
		}
	};
</script>

<script lang="ts">
	import '../app.css';
	import DeskNav from '$lib/desk-nav.svelte';
	import MobileNav from '$lib/mobile/mobile-nav.svelte';
	import MediaQuery from '$lib/media-query.svelte';
	import Footer from '$lib/footer.svelte';

	export let ftdata;	
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

<Footer {ftdata} />