<script lang="ts">
	export let ftdata;
</script>

<footer id="contact">
	<h4>{ftdata.footer.title}</h4>
	<div class="blurp_col">
		{#each ftdata.footer.blurbs as blurb}
			<div class="blurb">
				<a href={blurb.ref} target={blurb.target} rel="noopener noreferrer">
					<img src={blurb.icon.src} alt={blurb.icon.alt} srcset="" width="50" height="50" />
					<h3>{blurb.title}</h3>
				</a>
			</div>
		{/each}
	</div>
    <h4>Connect With Us</h4>
	<div class="blurp_col media">
		{#each ftdata.footer.socials as blurb}
			<div class="blurb">
				<a href={blurb.ref} target={blurb.target} rel="noopener noreferrer">
					<img src={blurb.icon.src} alt={blurb.icon.alt} srcset="" width="50" height="50" />
				</a>
			</div>
		{/each}
	</div>
	<div class="rights">
		<p>
			Copyright © <span>{ftdata.footer.copy}</span> <span>{new Date().getFullYear()}</span>. All
			Right Reserved.
		</p>
	</div>
</footer>

<style>
	h4 {
		font-size: var(--medium-font);
		font-weight: var(--bold);
		color: #fff;
	}

	h3 {
		font-size: var(--smal-font);
		font-weight: var(--bold);
		color: #fff;
	}

	p,
	span {
		font-size: var(--xsmal-font);
		font-weight: var(--medium);
		color: #fff;
	}

	footer {
		text-align: center;
		padding: 80px 0 0px;
		background-color: var(--default-footer-color);
	}

	.blurp_col {
		width: 80%;
		padding: 50px 0;
		margin: auto;
		display: flex;
		flex-direction: row;
		justify-content: space-evenly;
	}

	.blurb {
		text-align: center;
	}

	.media {
		padding: 50px 0;
		justify-content: center;
	}

	.media .blurb {
		margin: 0 30px;
	}

	.blurb a > img {
			margin-bottom: 20px;
		}

	.rights {
		background-color: #101010;
		padding: 20px;
	}

	@media (max-width: 850px) {
		.rights {
			padding-bottom: 75px;
		}

		.blurp_col {
			display: block;
		}

		.blurb {
			margin: 30px 0;
		}

		.media {
			display: flex;
		}

		.media .blurb {
			margin: 10px;
		}
	}
</style>
