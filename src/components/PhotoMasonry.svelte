<script>
	import photo1 from '$lib/assets/photo_1.jpg';
	import photo2 from '$lib/assets/photo_2.jpg';
	import photo3 from '$lib/assets/photo_3.jpg';
	import photo4 from '$lib/assets/photo_4.jpg';
	import photo5 from '$lib/assets/photo_5.jpg';
	import photo6 from '$lib/assets/photo_6.jpg';
	import photo7 from '$lib/assets/photo_7.jpg';
	import photo8 from '$lib/assets/photo_8.jpg';

	import Masonry from 'svelte-bricks';
	import Envelope from './Envelope.svelte';
</script>

<div class="container">
	<div id="title">
		<h1>ნანა და იოანე</h1>
	</div>
	<div>
		<Masonry
			items={[photo8, photo2, photo3, photo4, photo5, photo6, photo7, photo1]}
			minColWidth={100}
			maxColWidth={200}
			gap={3}
		>
			{#snippet children({ item })}
				<img src={item} alt="" width="100" style="border-radius: 5px;" />
			{/snippet}
		</Masonry>
	</div>
	<div>
		<Envelope/>
	</div>
</div>

<style>
	#title {
		display: flex;
		width: 100%;
		justify-content: center;
	}

	.container {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}
</style>
