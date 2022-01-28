<script context="module">
	
	export const load = async ({ url, fetch }) => {
		let path = url.params;
		let ref = `${import.meta.env.VITE_PLACE_ID}`; // Place ID
		let key = `${import.meta.env.VITE_MAPS_KEY}`; // Google Maps API key
		const res = await fetch(`../../post/landing-page.json`);
		const reviews = await fetch(
			`https://maps.googleapis.com/maps/api/place/details/json?reference=${ref}&key=${key}`
		);

		if (res.status === 404) {
			const error = new Error(`Oops! ${path} was not found`);
			return { status: 404, error };
		} else {
			const post = await res.json();
			const response = await reviews.json();
			return {
				props: {
					post,
					response
				}
			};
		}
	};
</script>

<script lang="ts">
	import Reviews from '$lib/google-reviews/reviews.svelte';

	export let post;
	export let response;
</script>

<svelte:head>
	<title>{post.title}</title>
	<link rel="icon" href={post.favicon.src} />
	<meta name="description" content={post.description} />
	<meta name="keywords" content={post.keywords} />
	<meta property="og:type" content={post.title} />
	<meta property="og:title" content={post.title} />
	<meta property="og:description" content={post.description} />
	<meta property="og:url" content={post.site_url} />
	<meta property="og:image" content={post.og_image} />
	<meta name="twitter:description" content={post.description}>
</svelte:head>

<section class="full_view">
	<div class="full_view_title">
		<h1>{post.full_header.title}</h1>
	</div>
	<div class="view_image">
		<img src={post.full_header.img.src} alt={post.full_header.img.alt} srcset="" />
	</div>
</section>

<section class="body_text" id="about">
	<div class="sml_text">
		<h2>{post.content.title}</h2>
		<p>{post.content.paragraph}</p>
	</div>
	<div class="gray_back">
		<div class="sml_text">
			<h2>{post.content_1.title}</h2>
			<p>{post.content_1.paragraph}</p>
		</div>

		<div class="blurp_col">
			{#each post.blurbs as blurb}
				<div class="blurb">
					<img src={blurb.img.src} alt={blurb.img.alt} srcset="" width="50" height="50" />
					<h3>{blurb.title}</h3>
					<span>{blurb.desc}</span>
				</div>
			{/each}
		</div>
	</div>
</section>

<section class="grid_temp" id="services">
	{#each post.grids as grid, i}
		<div class={grid.lean}>
			<div class="hold_img">
				<img src={grid.img.src} alt={grid.img.alt} srcset="" />
			</div>
			<div class="wrap_text">
				<div class="text_grid">
					<h3>{grid.title}</h3>
					<p>{grid.desc}</p>
				</div>
			</div>
		</div>
	{/each}
</section>

<section class="reviews" id="reviews">
	<Reviews {response} />
</section>

<style>
	h2, 
	h3 {
		margin-bottom: 25px;
	}

	.text_grid h3 {
		text-transform: capitalize;
		margin-bottom: 40px;
	}
	.full_view {
		width: 100%;
		height: 85vh;
		position: relative;
	}

	.full_view_title {
		width: 50%;
		margin: auto;
		padding-top: 5%;
		text-align: center;
	}

	.view_image {
		width: 100%;
		height: 100%;
		position: absolute;
		top: 0;
		left: 0;
		pointer-events: none;
		z-index: -1;
	}

	.view_image img {
		width: 100%;
		height: 100%;
		position: absolute;
		object-fit: cover;
		object-position: bottom;
	}

	.sml_text {
		width: 70%;
		margin: auto;
		padding: 80px 40px;
		text-align: center;
	}

	.blurp_col {
		width: 80%;
		margin: auto;
		display: flex;
		flex-wrap: wrap;
		flex-direction: row;
		justify-content: space-evenly;
	}

	.blurb {
		text-align: center;
	}

	.gray_back {
		padding-bottom: 80px;
		background-color: var(--default-grey-background);
	}

	.left,
	.right {
		display: flex;
		flex-wrap: wrap;
	}

	.right {
		flex-direction: row-reverse;
	}

	.hold_img img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.hold_img,
	.wrap_text {
		width: 50%;
	}

	.wrap_text {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.text_grid {
		width: 60%;
		margin: auto;
		text-align: left;
	}

	.reviews {
		position: relative;
		padding: 80px 40px;
	}

	@media (max-width: 850px) {
		.full_view_title {
			width: 85%;
			padding-top: 15%;
		}

		.sml_text {
			width: 100%;
			text-align: left;
		}

		.blurb {
			margin: 30px 0;
		}

		.hold_img,
		.wrap_text {
			width: 100%;
		}

		.text_grid {
			width: 100%;
			padding: 80px 40px;
		}
	}

	@media (min-width: 1440px) {
		.sml_text {
			width: 70%;
			padding: 100px 40px;
		}
	}
</style>
