<script lang="ts">
	import SimpleButton from '$lib/buttons/SimpleButton.svelte';

	interface entryConst {
		entry?: {
			subtitle?: string | undefined;
			headline?: string | undefined;
		};
		lead_button?: {
			url?: string | undefined;
			label?: string | undefined;
		};
		img?: {
			src?: string | undefined;
			alt?: string | undefined;
		};
	}

	interface Styling {
		v_position?: string | undefined;
		h_position?: string | undefined;
        offset_left?: string | undefined;
        offset_right?: string | undefined;
		align_text?: string | undefined;
	}

	export let EntryObj: entryConst;
	export let SectionStyle: Styling;

	function healinePosition(pos: string | undefined) {
		if (pos === undefined) {
			return 'center';
		} else if (pos === 'top') {
			return 'flex-start';
		} else if (pos === 'bottom') {
			return 'flex-end';
		} else if (pos === 'left') {
			return 'flex-start';
		} else if (pos === 'right') {
			return 'flex-end';
		} else {
			return 'center';
		}
	}
</script>

<div class="full_view">
	<div
		class="headLiner"
		style="
            --vertical-pos:
            {healinePosition(SectionStyle.v_position)}
            ;
            --horizontal-pos:
            {healinePosition(SectionStyle.h_position)}
            ;
            --offset-left:{SectionStyle.offset_left ? SectionStyle.offset_left: "0px"};
            --offset-right:{SectionStyle.offset_right ? SectionStyle.offset_right: "0px"};
            "
	>
		<div
			class="full_view_title"
			style="
                --text-align:{SectionStyle.align_text ? SectionStyle.align_text : 'center'};"
		>
        <div class="textBody">
			<h2>{EntryObj.entry.subtitle}</h2>
			<h1>{EntryObj.entry.headline}</h1>
        </div>
			{#if EntryObj.lead_button}
				<SimpleButton ButtonComp={EntryObj.lead_button} ButtonPos={"left"}/>
			{/if}
		</div>
	</div>
	<div class="view_image">
		<img src={EntryObj.img.src} alt={EntryObj.img.alt} srcset="" />
	</div>
</div>

<style lang="sass">
h1, h2
    --font-color: #fff
    color: var(--font-color)
    margin: 9px 0
    text-shadow: 0px 0px 10px rgba(225,225,225,.35)
    
h2
    font-size: calc( var(--medium-font) - 5.9px )

.full_view 
    width: 100%
    height: 85vh
    padding: 0 20px
    position: relative

.headLiner
    width: calc( 100% - (var(--offset-right) + var(--offset-left)))
    height: 100%
    margin: 0 var(--offset-right) 0 var(--offset-left)
    display: flex
    justify-content: var(--horizontal-pos)
    align-items: var(--vertical-pos)

.full_view_title 
    width: calc( 50% - (var(--offset-right) + var(--offset-left)))
    text-align: var(--text-align)

.textBody
    margin-bottom: 32px

.view_image 
    width: 100%
    height: 100%
    position: absolute
    top: 0
    left: 0
    pointer-events: none
    z-index: -1

.view_image img 
    width: 100%
    height: 100%
    position: absolute
    object-fit: cover
    object-position: bottom

@media (max-width: 850px) 
    h2
        font-size: calc( var(--medium-font) - 5.9px )
    .full_view_title 
        width: calc( 100% - (var(--offset-right) + var(--offset-left)))
    .view_image img 
        object-position: left
</style>
