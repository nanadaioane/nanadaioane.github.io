<script>
	import AnimationFrameSnow from "../components/AnimationFrameSnow.svelte";
	import PhotoCircle from "../components/PhotoCircle.svelte";
</script>

<div>
	<PhotoCircle />
	<AnimationFrameSnow />
</div>

<style>
	:global(body, html) {
		overflow: hidden !important;
		background-color: #ffc8dd !important;
	}
</style>
