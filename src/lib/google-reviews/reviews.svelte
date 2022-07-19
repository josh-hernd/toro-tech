<script lang="ts">
	export let response;
	let revArr;
	
	if (response.status == 'REQUEST_DENIED' || response.status == 'NOT_FOUND') {
		revArr = {status: response.status, res: response.error_message};
	} else {
		revArr = response.result.reviews;
	}

	let idx = 0;
</script>

<div class="reviews" id="reviews">
{#if revArr.status === 'REQUEST_DENIED' || revArr.status == 'NOT_FOUND'}
	<div class="reviews_wrap">
		<div class="head_review">
			<h3>Reviews From Real Customers</h3>
		</div>
		<code style="word-break: break-all;">{revArr.res}</code>
	</div>
{:else}
	<div class="reviews_wrap">
		<div class="head_review">
			<h3>Reviews From Real Customers</h3>
		</div>
		<div class="container">
			{#each revArr as reviews, i}
				{#if i == idx}
					<div class="review">
						<img src={reviews.profile_photo_url} alt={reviews.author_name} width="50px" />
						<h4>{reviews.author_name}</h4>
						<div class="stars">
							{#each { length: reviews.rating } as _}
								<img src="/svg/icons/stars.svg" alt="{reviews.rating} Rating" width="30" />
							{/each}
						</div>
						<div class="meta_text">
							<p>{reviews.text}</p>
						</div>
					</div>
				{/if}
			{/each}
			<div class="toggles">
				<button
					on:click={() => {
						idx--;
					}}
					disabled={idx == 0}
					class="previous"><img src="/svg/icons/previous.svg" alt="Previous" width="15" /></button
				>
				<button
					on:click={() => {
						idx++;
					}}
					disabled={idx == revArr.length - 1}
					class="next"><img src="/svg/icons/next.svg" alt="Next" width="15" /></button
				>
			</div>
		</div>
	</div>
{/if}
</div>
<style lang="sass">
h3,
h4
	text-shadow: 0px 0px 10px rgba(0, 0, 0, 0.25)

h4 
	margin: 10px 0
	
.reviews 
	position: relative
	padding: 80px 40px
	
.reviews_wrap 
	width: 100%
	padding: 80px
	position: relative
	margin: auto

.head_review 
	display: flex
	justify-content: space-between
	padding-bottom: 10px
	border-bottom: 2px solid #9b9b9b

.container 
	position: relative

button 
	height: 100%
	margin: 5px
	z-index: 10
	background-color: #0000
	background-repeat: no-repeat
	border: none
	cursor: pointer
	overflow: hidden
	outline: none

button:disabled 
	opacity: 0.2

.previous,
.next 
	z-index: 1

.previous 
	position: absolute
	top: 0%
	left: 0

.next 
	position: absolute
	top: 0%
	right: 0

.review 
	text-align: center
	padding: 25px 0
	img
		-webkit-filter: drop-shadow(0px 0px 5px rgba(0, 0, 0, 0.6))
		filter: drop-shadow(0px 0px 5px rgba(0, 0, 0, 0.6))
.meta_text 
	width: 70%
	margin: auto

.stars 
	text-align: center
	padding: 10px
	img
		-webkit-filter: drop-shadow(0px 0px 5px rgba(0, 0, 0, 0.1))
		filter: drop-shadow(0px 0px 5px rgba(0, 0, 0, 0.1))
@media (min-width: 1440px) 
	
	.reviews_wrap 
		width: 70%
		padding: 80px 20px
	
@media (max-width: 850px) 
	.reviews_wrap 
		padding: 40px 20px
		text-align: center
	
	.head_review 
		display: block
	
	.meta_text 
		width: 100%
	
	.toggles 
		padding: 15px 0
	
	.previous 
		left: -45px
	
	.next 
		right: -45px
</style>
