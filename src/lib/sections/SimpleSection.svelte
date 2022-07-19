<script lang="ts">
import SimpleButton from "$lib/buttons/SimpleButton.svelte";

interface BuildContent {
    entry?: {title?: string | undefined; desc?: string | undefined;}
    lead_button?: {url?: string | undefined; label?: string | undefined;}
    styled?: {bgImg?: string | undefined;}
}
export let Content: BuildContent;
</script>
<div class="wrap">
    <div class="content">
        <h2>{Content.entry.title}</h2>
        <p>{Content.entry.desc}</p>
        <SimpleButton ButtonComp={Content.lead_button} ButtonPos={"center"}/>
    </div>
    <div class="backSrc"><img src={Content.styled.bgImg} alt="Background"></div>
</div>

<style lang="sass">
h2,
p
    color: #fff
    text-shadow: 0px 0px 10px rgba(225, 225, 225, 0.35)
    
.wrap
    position: relative
    padding: 180px 20px
    text-align: center
    display: flex
    justify-content: center

.backSrc
    width: 100%
    height: 100%
    position: absolute
    inset: 0 0
    background: #0A232A
    z-index: -1
    img
        width: 100%
        height: 100%
        display: block
        object-fit: cover
        opacity: 0.47
</style>