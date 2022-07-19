<script lang="ts">
	export let burgerColor;
	export let menuColor;
	export let duration;
	export let open;
	
</script>
<svg width="783" height="785" viewBox="0 0 783 782" fill="none" xmlns="http://www.w3.org/2000/svg">
	<circle cx="391.367" cy="390.602" r="367.875" style="color: {open ? menuColor : burgerColor};"/>
	<g class="ani" style="color: {open ? menuColor : burgerColor}; fill: {duration}s ease-in-out;">
		<path
			d="M368.692 9.93323C170.367 21.5814 12.8413 185.031 10.6398 385.758H0C2.16707 182.642 159.054 16.6314 358.386 0L368.692 9.93323Z"
		/>
		<path
			d="M772.094 394.255H782.734C780.917 565.658 668.921 710.642 514.213 761.742L505.009 753.522C658.503 705.585 770.254 563.106 772.094 394.255Z"
		/>
		<path
			d="M367.888 770.058L378.559 781.204C212.616 775.869 72.7661 667.235 21.2083 517.503L31.4222 514.477C80.5514 656.588 211.468 760.542 367.888 770.058Z"
		/>
		<path
			d="M559.163 48.1421V36.3223C674.178 90.9832 758.307 200.092 778.235 330.336L768.051 334.176C749.539 208.225 669.359 102.329 559.163 48.1421Z"
		/>
	</g>
</svg>

<style lang="sass">
svg
	-webkit-filter: drop-shadow(0px 0px 5px rgb(0 0 0 / 0.15))
	filter: drop-shadow(0px 0px 5px rgb(0 0 0 / 0.15))
svg path, svg circle 
	fill: currentColor

.ani 
	animation-duration: 6.5s 
	animation-iteration-count: infinite 
	animation-name: rotation 
	transform-origin: 50% 50% 
@keyframes rotation 
		from 
			-webkit-transform: rotate(0deg) 
		to 
			-webkit-transform: rotate(360deg)
</style>
