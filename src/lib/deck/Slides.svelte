<script>
	import 'reveal.js/dist/reveal.css';
	import 'reveal.js/dist/theme/black.css';
	import Reveal from 'reveal.js';
	import { onMount } from 'svelte';
	import Presentation from './Presentation.svelte';

	onMount(() => {
		const deck = new Reveal({
			progress: true
		});

		deck.initialize();
	});
</script>

<div class="reveal">
	<div class="slides">
		<Presentation />
	</div>
</div>
