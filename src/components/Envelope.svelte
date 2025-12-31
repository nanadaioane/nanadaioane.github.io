<script>
	import heart from '$lib/assets/heart.png';

	let is_opened = $state(false);
	let opened_style = $derived(is_opened ? 'open': 'close')

	function toggleOpened() {
		is_opened = !is_opened;
	}
</script>

<!-- svelte-ignore a11y_click_events_have_key_events, a11y_no_static_element_interactions (because of reasons) -->
<div class="envlope-wrapper" onclick={toggleOpened}>
	<div id="envelope" class="{opened_style}">
		<div class="front flap"></div>
		<div class="front pocket"></div>
		<div class="letter">
			<p>
				ნანა ჩემი სიყვარულის და ბედნიერების წყარო ხარ. როგორ მიხარია რომ მეორე ახალი წელია რომელსაც
				შენთან ერთად ვხვდები. ყველაფერს საუკეთესოს გისურვებ და იმედი მაქვს იქამდე შევხდებით ახალ
				წლებს ერთად ერთმანეთის გვერდში, სანამ ბებრები არ დავილევით.
			</p>

			<p>
				უსაზღვრო სიყვარულით, <br> შენი გოჭისგან 🐷
			</p>

			<img src="{heart}" alt="" width="70px" style="position: absolute; bottom: 20px; right: 10px;">
		</div>
		<div class="hearts">
			<div class="heart a1"></div>
			<div class="heart a2"></div>
			<div class="heart a3"></div>
		</div>
	</div>
</div>

<style lang="scss">
	$color-env: #ffafcc;
	$color-env2: darken($color-env, 3%);
	$color-flap: darken($color-env, 20%);
	$color-bg: lighten($color-env, 48%);
	$color-heart: #d00000;

	$env-border-radius: 6px;
	$env-width: 280px;
	$env-height: 180px;
	$heart-width: 50px;

	#envelope {
		position: relative;
		width: $env-width;
		height: $env-height;
		border-bottom-left-radius: $env-border-radius;
		border-bottom-right-radius: $env-border-radius;
		margin-left: auto;
		margin-right: auto;
		top: 150px;
		background-color: $color-flap;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
	}
	.front {
		position: absolute;
		width: 0;
		height: 0;
		z-index: 3;
	}
	.flap {
		border-left: ($env-width / 2) solid transparent;
		border-right: ($env-width / 2) solid transparent;
		border-bottom: ($env-height / 2) - 8 solid transparent; /* a little smaller */
		border-top: ($env-height / 2) + 8 solid $color-flap; /* a little larger */
		transform-origin: top;
		pointer-events: none;
	}
	.pocket {
		border-left: ($env-width / 2) solid $color-env;
		border-right: ($env-width / 2) solid $color-env;
		border-bottom: ($env-height / 2) solid $color-env2;
		border-top: ($env-height / 2) solid transparent;
		border-bottom-left-radius: $env-border-radius;
		border-bottom-right-radius: $env-border-radius;
	}
	.letter {
		position: relative;
		background-color: #fff;
		width: 90%;
		margin-left: auto;
		margin-right: auto;
		height: 90%;
		top: 5%;
		border-radius: $env-border-radius;
		box-shadow: 0 2px 26px rgba(0, 0, 0, 0.12);

		box-sizing: border-box;
		padding: 1rem;
		padding-top: 0.1rem;
		font-size: 0.7rem;
		overflow: hidden;
	}
	.letter:after {
		content: '';
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
	}
	.words {
		position: absolute;
		left: 10%;
		width: 80%;
		height: 14%;
		background-color: #eeeff0;
	}
	.open .flap {
		transform: rotateX(180deg);
		transition:
			transform 0.4s ease,
			z-index 0.6s;
		z-index: 1;
	}
	.close .flap {
		transform: rotateX(0deg);
		transition:
			transform 0.4s 0.6s ease,
			z-index 1s;
		z-index: 5;
	}
	.close .letter {
		transform: translateY(0px);
		transition:
			transform 0.4s ease,
			z-index 1s;
		z-index: 1;
	}
	.open .letter {
		transform: translateY(-($env-height / 3));
		transition:
			transform 0.4s 3s ease,
			z-index 0.0s 3.4s,
			height 0.0s 3.4s;
		z-index: 3;
		height: 120%;
	}
	.hearts {
		position: absolute;
		top: ($env-height / 2);
		left: 0;
		right: 0;
		z-index: 2;
	}
	.heart {
		position: absolute;
		bottom: 0;
		right: 10%;
		pointer-events: none;
	}

	.heart:before,
	.heart:after {
		position: absolute;
		content: '';
		left: $heart-width;
		top: 0;
		width: $heart-width;
		height: ($heart-width * 1.6);
		background: $color-heart;
		border-radius: $heart-width $heart-width 0 0;
		transform: rotate(-45deg);
		transform-origin: 0 100%;
		pointer-events: none;
	}
	.heart:after {
		left: 0;
		transform: rotate(45deg);
		transform-origin: 100% 100%;
	}
	.close .heart {
		opacity: 0;
		animation: none;
	}
	.a1 {
		left: 20%;
		-webkit-transform: scale(0.6);
		-moz-transform: scale(0.6);
		transform: scale(0.6);
		opacity: 1;
		-webkit-animation:
			slideUp 7s linear 1,
			sideSway 2s ease-in-out 6 alternate,
			dissapear 2s linear 7s 1;
		-moz-animation:
			slideUp 7s linear 1,
			sideSway 7s ease-in-out 6 alternate,
			dissapear 7s linear 7s 1;
		animation-fill-mode: forwards;
		animation-delay: 0.7s;
	}
	.a2 {
		left: 55%;
		-webkit-transform: scale(1);
		-moz-transform: scale(1);
		transform: scale(1);
		opacity: 1;
		-webkit-animation:
			slideUp 7s linear 1,
			sideSway 2s ease-in-out 6 alternate,
			dissapear 2s linear 7s 1;
		-moz-animation:
			slideUp 7s linear 1,
			sideSway 7s ease-in-out 6 alternate,
			dissapear 7s linear 7s 1;
		animation-fill-mode: forwards;
		animation-delay: 0.7s;
	}
	.a3 {
		left: 10%;
		-webkit-transform: scale(0.8);
		-moz-transform: scale(0.8);
		transform: scale(0.8);
		opacity: 1;
		-webkit-animation:
			slideUp 7s linear 1,
			sideSway 2s ease-in-out 6 alternate,
			dissapear 7s linear 7s 1;
		-moz-animation:
			slideUp 7s linear 1,
			sideSway 2s ease-in-out 6 alternate,
			dissapear 7s linear 7s 1;
		animation-fill-mode: forwards;
		animation-delay: 0.7s;
	}

	@-webkit-keyframes slideUp {
		0% {
			top: 0;
		}
		100% {
			top: -600px;
		}
	}
	@keyframes slideUp {
		0% {
			top: 0;
		}
		100% {
			top: -600px;
		}
	}
	@-webkit-keyframes sideSway {
		0% {
			margin-left: 0px;
		}
		100% {
			margin-left: 50px;
		}
	}
	@keyframes sideSway {
		0% {
			margin-left: 0px;
		}
		100% {
			margin-left: 50px;
		}
	}
	@-webkit-keyframes dissapear {
		0% {
			opacity: 100%;
		}
		100% {
			opacity: 0%;
		}
	}
	@keyframes dissapear {
		0% {
			opacity: 100%;
		}
		100% {
			opacity: 0%;
		}
	}

	body {
		background-color: $color-bg;
	}
	.envlope-wrapper {
		height: ($env-height + 200px);
	}
	.reset {
		text-align: center;
	}
	.reset button {
		font-weight: 800;
		font-style: normal;
		transition: all 0.1s linear;
		-webkit-appearance: none;
		background-color: transparent;
		border: solid 2px $color-env;
		border-radius: 4px;
		color: $color-env;
		display: inline-block;
		font-size: 14px;
		text-transform: uppercase;
		margin: 5px;
		padding: 10px;
		line-height: 1em;
		text-decoration: none;
		min-width: 120px;
		cursor: pointer;
	}
	.reset button:hover {
		background-color: $color-env;
		color: #fff;
	}
</style>
