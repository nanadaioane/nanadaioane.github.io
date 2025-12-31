<script>
	import photo1 from '$lib/assets/photo_1.jpg';
	import photo2 from '$lib/assets/photo_2.jpg';
	import photo3 from '$lib/assets/photo_3.jpg';
	import photo4 from '$lib/assets/photo_4.jpg';
	import photo5 from '$lib/assets/photo_5.jpg';
	import photo6 from '$lib/assets/photo_6.jpg';
	import photo7 from '$lib/assets/photo_7.jpg';
	import photo8 from '$lib/assets/photo_8.jpg';
</script>

<div class="container">
	<div class="oval-container">
		<div class="circle-container">
			{#each [photo8, photo2, photo3, photo4, photo5, photo6, photo7, photo1] as photo}
				<div class="circle-item">
					<img src={photo} alt="" />
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	.container {
		display: flex;
		justify-content: center; /* Centers horizontally */
		align-items: center; /* Centers vertically */
		height: 100vh; /* Takes up the full height of the viewport */
		width: 100vw; /* Takes up the full width of the viewport */
		/* Optional: add a background to see the container */
	}

	.circle-item {
		width: fit-content;
		position: absolute;
		top: 50%;
		left: 50%;
		margin: -40px; /* Half the image size (to center the image itself) */
		object-fit: cover;
	}

	.circle-item > img {
		border-radius: 10px; /* Makes the images circular */
		height: 120px;
	}

	.circle-item:nth-child(1) {
		transform: rotate(0deg) translate(300px) rotate(0deg);
	}

	.circle-item:nth-child(2) {
		transform: rotate(45deg) translate(300px) rotate(-45deg);
	}

	.circle-item:nth-child(3) {
		transform: rotate(90deg) translate(300px) rotate(-90deg);
	}

	.circle-item:nth-child(4) {
		transform: rotate(135deg) translate(300px) rotate(-135deg);
	}

	.circle-item:nth-child(5) {
		transform: rotate(180deg) translate(300px) rotate(-180deg);
	}

	.circle-item:nth-child(6) {
		transform: rotate(225deg) translate(300px) rotate(-225deg);
	}

	.circle-item:nth-child(7) {
		transform: rotate(270deg) translate(300px) rotate(-270deg);
	}

	.circle-item:nth-child(8) {
		transform: rotate(315deg) translate(300px) rotate(-315deg);
	}
</style>
