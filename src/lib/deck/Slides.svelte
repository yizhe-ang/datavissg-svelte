<script>
	import 'reveal.js/dist/reveal.css';
	import 'reveal.js/dist/theme/black.css';
	import Reveal from 'reveal.js';
	import { onMount } from 'svelte';
	import Presentation from './Presentation.svelte';

	onMount(() => {
		const deck = new Reveal({ disableLayout: false, autoAnimateDuration: 0.5 });

		deck.initialize();
	});
</script>

<div class="reveal">
	<div class="slides">
		<Presentation />
	</div>
</div>

<style>
	:root {
		--main-color: hsl(20, 68%, 85%);
		/* --secondary-color: #8bd3dd; */
		--secondary-color: #20c9df;
		--tertiary-color: #f582ae;

		--r-background-color: #fef6e4;
		--r-main-color: #172c66;
		--r-heading-color: #001858;
		--r-link-color: var(--secondary-color);
		--r-link-color-hover: var(--r-main-color);

		--r-main-font: 'Montserrat Variable', sans-serif;
		--r-heading-font: 'Montserrat Variable', sans-serif;
		--r-heading-text-transform: none;
		--r-heading1-size: 1.6em;
	}

	:global(.reveal .progress) {
		height: 10px;
	}
</style>
