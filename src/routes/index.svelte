<script context="module">
	export const load = async ({ url, fetch }) => {
		let path = url.params;
		let ref = `${import.meta.env.VITE_PLACE_ID}`; // Place ID
		let key = `${import.meta.env.VITE_MAPS_KEY}`; // Google Maps API key
		const reviews = await fetch(
			`https://maps.googleapis.com/maps/api/place/details/json?reference=${ref}&key=${key}`
		);

		if (reviews.status === 404) {
			const error = new Error(`Oops! ${path} was not found`);
			return { status: 404, error };
		} else {
			const response = await reviews.json();
			return {
				props: {
					response
				}
			};
		}
	};
</script>

<script lang="ts">
	import { LandingPage } from './the-content/content';
	import FullSection from '$lib/sections/FullSection.svelte';
	import TwoColSection from '$lib/sections/TwoColSec.svelte';
	import Reviews from '$lib/google-reviews/reviews.svelte';
	import FullTwoSection from '$lib/sections/FullTwoSection.svelte';
	import SimpleSection from '$lib/sections/SimpleSection.svelte';

	export let response;
</script>

<svelte:head>
	<title>{LandingPage.title}</title>
	<link rel="icon" href={LandingPage.favicon.src} />
	<meta name="description" content={LandingPage.description} />
	<meta name="keywords" content={LandingPage.keywords} />
	<meta property="og:type" content={LandingPage.title} />
	<meta property="og:title" content={LandingPage.title} />
	<meta property="og:description" content={LandingPage.description} />
	<meta property="og:url" content={LandingPage.site_url} />
	<meta property="og:image" content={LandingPage.og_image} />
	<meta name="twitter:description" content={LandingPage.description} />
</svelte:head>

<FullSection
	EntryObj={LandingPage.full_header}
	SectionStyle={{
		v_position: 'center',
		h_position: 'left',
		offset_left: '50px',
		align_text: 'left'
	}}
/>
<TwoColSection EntryObj={LandingPage.content} />

<FullTwoSection GridsObj={LandingPage.grids} />

<SimpleSection Content={LandingPage.opt_in} />

<Reviews {response} />
