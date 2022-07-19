<script lang="ts">
	import BlurbSection from './BlurbSection.svelte';

	interface EntryInter {
		sideImg?: {
			smallImg?: {src?: string | undefined; alt?: string | undefined}
			largeImg?: {src?: string | undefined; alt?: string | undefined}
		}
		entry?: { announcer?: string | undefined; title?: string | undefined; paragraph?: string | undefined };
		blurbs?: [
			{
				img?: { 
					src?: string | undefined; 
					alt?: string | undefined 
				}
				title?: string | undefined;
				desc?: string | undefined;
			}
		];
	}
	export let EntryObj: EntryInter;
</script>

<div class="colWrap">
	<div class="col">
		<div class="displace">
		<div class="smlImg"><img src={EntryObj.sideImg.smallImg.src} alt={EntryObj.sideImg.smallImg.alt} srcset=""></div>
		<div class="lrgImg"><img src={EntryObj.sideImg.largeImg.src} alt={EntryObj.sideImg.largeImg.alt} srcset=""></div>
	</div>
</div>
	<div class="body_text col" id="about">
		<div class="announce">
			<h4>{EntryObj.entry.announcer}</h4>
		</div>
		<div class="sml_text">
			<h2>{EntryObj.entry.title}</h2>
			<p>{EntryObj.entry.paragraph}</p>
		</div>
	</div>
</div>

{#if EntryObj.blurbs}
	<BlurbSection Blurbs={EntryObj.blurbs} />
{/if}

<style lang="sass">
@use '../abstract/dynamicBreaks' as *

.colWrap
	display: flex
	padding: 180px 20px 100px
	@include dynamicpoint($max: 850px)
		flex-direction: column
		padding-top: 150px
.col
	width: 50%
	@include dynamicpoint($max: 850px)
		width: 100%
		text-align: center
		&:first-child
			margin-bottom: 40px
h2
	text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.25)
p
	text-align: justify
img
	width: 100%
	display: block

.displace
	position: relative
	width: 100%
	margin: auto
	
.smlImg, .lrgImg
	box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2)
	
.smlImg
	width: 100%
	max-width: 182px
	position: absolute
	inset: -80px auto auto 60px
	z-index: -1
	@include dynamicpoint($max: 850px)
		max-width: 100px
		inset: -50px auto auto 30px

.lrgImg
	width: 100%
	max-width: 412px
	margin: auto
	@include dynamicpoint($max: 850px)
		max-width: 250px

.announce
	width: max-content
	padding: 12px 50px
	background: #357091
	box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3)
	h4
		color: #fff
	@include dynamicpoint($max: 850px)
		margin: auto

.sml_text 
	width: 70%
	margin-right: auto
	padding: 80px 0px
	text-align: left
	@include dynamicpoint($max: 850px)
		width: 95%
		margin: auto
		text-align: center
</style>
