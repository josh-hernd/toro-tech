<script lang="ts">
	interface GridsConst {
		lean?: string | undefined;
		announcer?: string | undefined;
		img?: { src?: string | undefined; alt?: string | undefined };
		title?: string | undefined;
		desc?: string | undefined;
	}

	export let GridsObj: GridsConst[];
</script>

<div class="grid_temp" id="services">
	{#each GridsObj as grid, i}
		<div class="grid {grid.lean}">
			<div class="hold_img">
				<img src={grid.img.src} alt={grid.img.alt} srcset="" />
			</div>
			<div class="wrap_text">
				{#if grid.announcer}
					<div class="announce">
						<h4>{grid.announcer}</h4>
					</div>
				{/if}
				<div class="text_grid">
					<h3>{grid.title}</h3>
					<p>{grid.desc}</p>
                    <div class="numbered">
                        <h6>0{(3 + i) - 2}</h6>
                    </div>
				</div>
			</div>
		</div>
	{/each}
</div>

<style lang="sass">
@use '../abstract/dynamicBreaks' as *
h3
    text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.25)
h6
    color: #fff
    font-weight: 800
    font-size: 19rem
    -webkit-text-stroke: 2px rgba(0, 0, 0, 0.05)
    @include dynamicpoint($max: 850px)
        font-size: 10rem
p
    text-align: justify
.grid
    padding: 60px 0

.hold_img img 
    width: 100%
    height: 100%
    object-fit: cover

.hold_img,
.wrap_text 
    width: 50%
    @include dynamicpoint($max: 850px)
        width: 100%

.wrap_text 
    display: flex
    flex-direction: column
    padding: 0 90px
    @include dynamicpoint($max: 850px)
        padding: 0

h3 
    margin-bottom: 25px

.text_grid h3 
    text-transform: capitalize
    margin-bottom: 40px


.left,
.right 
    display: flex
    flex-wrap: wrap

.right 
    flex-direction: row-reverse

.text_grid 
    position: relative
    margin: auto
    text-align: left
    @include dynamicpoint($max: 850px)
        width: 100%
        padding: 130px 40px 0
        // overflow: hidden

.announce
    width: max-content
    padding: 12px 50px
    background: #357091
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3)
    h4
        color: #fff
    @include dynamicpoint($max: 850px)
        margin: 40px auto 0

.numbered
    width: max-content
    position: absolute
    inset: -199px -10px
    z-index: -1
    @include dynamicpoint($max: 850px)
        inset: 30px 80px
</style>
