<script>
	import AnimationFrameSnow from "../components/AnimationFrameSnow.svelte";
	import PhotoMasonry from "../components/PhotoMasonry.svelte";
</script>

<div>
	<PhotoMasonry />
	<AnimationFrameSnow />
</div>

<style>
	:global(body, html) {
		overflow: hidden !important;
		background-color: #ffc8dd !important;
	}
</style>
