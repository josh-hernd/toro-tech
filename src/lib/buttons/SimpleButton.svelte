<script lang="ts">
interface btnConst {
    url?: string | undefined;
    label?: string | undefined;
}

export let ButtonComp: btnConst;

export let ButtonPos: string | undefined;

function buttonPosition(pos: string | undefined) {
		if (pos === undefined) {
			return 'auto';
		} else if (pos === 'left') {
			return '10px 0';
		} else if (pos === 'right') {
			return '10px 0 10px auto';
		} else {
			return 'auto';
		}
	}
</script>
<div class="buttonWrap" style="--button-position:{buttonPosition(ButtonPos)};">
    <a href={ButtonComp.url}>{ButtonComp.label}</a>
</div>

<style lang="sass">
.buttonWrap
    --button-position: 10px 0
    width: max-content
    position: relative
    margin: var(--button-position)
    box-shadow: 0px 0px 10px rgba(225,225,225,.2)
    &:hover
        box-shadow: 0px 0px 10px rgba(225,225,225,.35)

a
    color: #fff
    font-size: var(--smal-font)
    font-weight: var(--bold)
    display: block
    padding: 12px 50px
    background: #357091
</style>