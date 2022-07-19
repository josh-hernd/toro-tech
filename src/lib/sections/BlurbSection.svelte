<script lang="ts">
	interface blurbConst {
		img?: { src?: string | undefined; alt?: string | undefined };
		title?: string | undefined;
		desc?: string | undefined;
	}
	export let Blurbs: blurbConst[];
</script>

<div class="color_scheme">
	<div class="blurp_col">
		{#each Blurbs as blurb}
			<div class="blurb">
				<img src={blurb.img.src} alt={blurb.img.alt} srcset="" width="50" height="50" />
				<h3>{blurb.title}</h3>
				<span>{blurb.desc}</span>
			</div>
		{/each}
	</div>
</div>

<style lang="sass">
@use '../abstract/dynamicBreaks' as *
h3, span
    color: #fff
    text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.35)
.color_scheme 
    padding: 80px 0
    background-color: var(--default-accent)

.blurp_col 
    width: 80%
    margin: auto
    display: flex
    flex-wrap: wrap
    flex-direction: row
    justify-content: space-evenly

.blurb 
    margin: auto 15px
    text-align: center
    img
        -webkit-filter: drop-shadow(0px 0px 5px rgba(0,0,0,.6))
        filter: drop-shadow(0px 0px 5px rgba(0,0,0,.6))
    @include dynamicpoint($max: 850px)
        margin-bottom: 30px
    
</style>
