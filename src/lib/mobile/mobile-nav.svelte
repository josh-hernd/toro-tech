<script lang="ts">
	import Burger from './burger.svelte';
	import NavElipse from './nav-elipse.svelte';

	let open = false;
	const styles = {
	duration: 0.4,
	burgerColor: '#357091',
	menuColor: '#357091'
	}
</script>

<header>
	<div class="wrap">
		<div id="logo"><a href="#top"><img src="/svg/logo-main.svg" alt="Logo" srcset="" /></a></div>
	</div>
</header>

<mobile-nav>
	<Burger bind:open {...styles}/>
</mobile-nav>


<nav class:open>

	<div id="menu">
		<ul>
			<li><a href="#top">Home</a></li>
			<li><a href="#about">About Us</a></li>
			<li><a href="#services">Our Services</a></li>
			<li><a href="#reviews">Our Customers</a></li>
			<li><a href="#contact">Contact Us</a></li>
		</ul>
	</div>

	<div class="anim_nav">
		<NavElipse {open} {...styles}/>
	</div>
</nav>

<style lang="sass">
header 
	position: fixed 
	width: 100% 
	top: 0 
	left: 0 
	background-color: var(--default-header-color) 
	box-shadow: 0px 1px 5px rgba(0, 0, 0, 0.15) 
.wrap 
	padding: 10px 10px 
	text-align: center 
mobile-nav 
	position: fixed 
	width: 100% 
	padding: 10px 30px 
	bottom: 0 
	text-align: right 
	background-color: var(--default-header-color) 
	box-shadow: 0px -1px 5px rgba(0, 0, 0, 0.15) 
nav 
	width: 100% 
	position: fixed 
	bottom: 65px 
	z-index: 5 
	opacity: 0 
	transform: translate(0px, 500px) 
	transition: transform 0.4s ease-in-out, opacity 0.4s ease-in-out 
	&.open 
		opacity: 1 
		transform: translate(0px, 0px) 
header,
	mobile-nav 
	z-index: 6 
#menu 
	position: absolute 
	bottom: 30px 
	right: 30px 
	z-index: 5 
	transform: translate(0px, 200px) 
	transition: transform 0.4s ease-in-out 
.open 
	#menu 
		transition-delay: 0.1s 
		transform: translate(0px, 0px) 
a 
	font-size: 19px 
	font-weight: var(--medium) 
	color: #fff 
li 
	margin: 10px 0 
.anim_nav 
	position: absolute 
	bottom: -350px 
	right: -350px 
	pointer-events: none 
</style>
