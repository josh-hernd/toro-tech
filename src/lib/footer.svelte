<script lang="ts">
	interface ftData {
		title?: string;
		blurbs?: [
			{
				icon?: { src?: string; alt?: string };
				title?: string;
				ref?: string;
				target?: string;
			}
		];
		hours?: {
			title?: string;
			list?: [
				{
					day?: string;
					time?: string;
				}
			];
		};

		socials?: [
			{
				icon?: { src?: string; alt?: string };
				ref?: string;
				target?: string;
			}
		];
		copy?: string;
	}
	export let footerData: ftData;
</script>

<footer id="contact">
	<div class="flexr">
		<div class="cols">
			<h4>{footerData.title}</h4>
			<div class="blurp_col">
				{#each footerData.blurbs as blurb}
					<div class="blurb">
						<a href={blurb.ref} target={blurb.target} rel="noopener noreferrer">
							<img src={blurb.icon.src} alt={blurb.icon.alt} srcset="" width="50" height="50" />
							<h3>{blurb.title}</h3>
						</a>
					</div>
				{/each}
			</div>
		</div>
		<div class="cols">
			<h4>{footerData.hours.title}</h4>
			<table>
				<tbody>
					{#each footerData.hours.list as hour}
						<tr>
							<td>{hour.day}</td>
							<td>{hour.time}</td>
						</tr>
					{/each}
				</tbody>
			</table>
		</div>
		<div class="cols">
			<h4>Connect With Us</h4>
			<div class="blurp_col media">
				{#each footerData.socials as blurb}
					<div class="blurb">
						<a href={blurb.ref} target={blurb.target} rel="noopener noreferrer">
							<img src={blurb.icon.src} alt={blurb.icon.alt} srcset="" width="50" height="50" />
						</a>
					</div>
				{/each}
			</div>
		</div>
	</div>
	<div class="rights">
		<p>
			Copyright © <span>{footerData.copy}</span> <span>{new Date().getFullYear()}</span>. All Right
			Reserved.
		</p>
	</div>
</footer>

<style lang="sass">
@use 'abstract/dynamicBreaks' as *
h4 
	font-size: var(--medium-font)
	font-weight: var(--bold)
	color: #fff

h3 
	font-size: var(--smal-font)
	font-weight: var(--bold)
	color: #fff
	@include dynamicpoint($max: 910px)
		font-size: calc(var(--smal-font) - 3px )
p,
span,
td
	font-size: var(--xsmal-font)
	font-weight: var(--medium)
	color: #fff

footer 
	padding: 80px 0px 0px
	background-color: var(--default-footer-color)

.flexr
	padding: 0px 20px
	display: flex
	justify-content: space-evenly
	@include dynamicpoint($max: 910px)
		width: 80%
		margin: auto
		flex-direction: column
		justify-content: center

.cols
	padding: 40px 0

.blurp_col 
	width: auto
	padding-otp: 50px
	margin: auto
	display: flex
	flex-direction: column

.blurb
	margin-bottom: 30px
	a
		display: flex
		align-items: center
	@include dynamicpoint($max: 850px)
		margin: 30px 0

.media 
	padding: 50px 0
	flex-direction: row

.media .blurb 
	margin: 0 30px

.blurb a > img 
		margin-right: 20px

.rights 
	background-color: #357091
	padding: 20px
	text-align: center
	@include dynamicpoint($max: 850px)
		padding-bottom: 75px

@media (max-width: 850px)
	.blurp_col 
		display: block

	.media 
		display: flex

	.media .blurb 
		margin: 10px
</style>
