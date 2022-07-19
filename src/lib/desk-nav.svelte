<header>
	<div class="wrap">
		<div id="logo"><a href="#top"><img src="/svg/logo-main.svg" alt="Logo" srcset="" /></a></div>
		<nav>
			<ul>
				<li><a href="#top">Home</a></li>
				<li><a href="#about">About Us</a></li>
				<li><a href="#services">Our Services</a></li>
				<li><a href="#reviews">Our Customers</a></li>
				<li><a href="#contact">Contact Us</a></li>
			</ul>
		</nav>
	</div>
</header>

<style lang="sass">
	header 
		position: fixed
		width: 100%
		top: 0
		left: 0
		background-color: var(--default-header-color)
		box-shadow: 0px 1px 5px rgba(0, 0, 0, 0.15)

	.wrap 
		display: flex
		justify-content: space-between
		align-items: center
		padding: 28px 80px

	#logo img 
		user-select: none

	ul 
		display: flex
		justify-content: space-around

	li 
		margin: 0 10px

	a 
		font-size: 16px
		font-weight: var(--medium)
</style>
