<script>
	import Chart from '$lib/chart/Chart.svelte';
	import Slide from './Slide.svelte';
	import Source from './Source.svelte';

	const bgImgUrl =
		'https://images.squarespace-cdn.com/content/v1/5784fde5be6594ad5e37b456/1513327514230-V4TBDQX6PVGYTUQNA3TN/ComeMakanMakan.jpg?format=2500w';
</script>

<!-- Introduce our dataset? -->
<Slide
	attrs={{
		'data-background-image': bgImgUrl
	}}
>
	<Source
		id={'source'}
		context={'Illustration by'}
		linkText={'Lee Xin Li'}
		linkUrl={'http://leexinli.com/2017/12/15/-makan-makan'}
	/>
</Slide>

<Slide
	attrs={{
		'data-background-image': bgImgUrl
	}}
>
	<div>
		<h2>
			Let's Visualize the<br /> Nutritional Data of<br /> Hawker Food!
		</h2>
	</div>
	<Source
		id={'source'}
		context={'Illustration by'}
		linkText={'Lee Xin Li'}
		linkUrl={'http://leexinli.com/2017/12/15/-makan-makan'}
	/>
</Slide>

<Slide>
	<Chart />
	<Source
		context={'Data from'}
		linkText={`KK Women's and Children's Hospital`}
		linkUrl={'https://www.healthxchange.sg/food-nutrition/food-tips/best-worst-singapore-hawker-chinese-food-dim-sum-char-kway-teow'}
	/>
</Slide>

<style>
	div {
		height: 100%;
		width: 100%;
		display: grid;
		align-content: center;
	}

	h2 {
		text-align: left;
		margin: auto 0;
		line-height: 1.3;
	}
</style>
