<script>
	import '../app.css';
	import Chart from '$lib/chart/Chart.svelte';

	// import Slides from '$lib/deck/Slides.svelte';
</script>

<Chart />

<!-- <Slides /> -->

<style>
	/* :global(body) {
		font-family: sans-serif;
		background-color: #f5f5f4;
		color: #44403c;
	} */

  :global(body) {
		background-color: #fef6e4;
		color: #44403c;
    font-family: 'Montserrat Variable', sans-serif;
	}

	:global(select) {
		background-color: white;
		color: black;
    font-family: 'Montserrat Variable', sans-serif;
	}
</style>
