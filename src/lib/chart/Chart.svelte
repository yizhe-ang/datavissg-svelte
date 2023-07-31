<script>
	import { fade } from 'svelte/transition';
	import { scaleLinear, max } from 'd3';

	// Import data
	import data from './data.json';

	// To store chart dimensions
	let width;
	let height;

	let hoveredData;

	const variables = ['carbs(g)', 'cholesterol(mg)', 'fat(g)', 'kcal', 'protein(g)', 'sodium(mg)'];

	let selectedType;
	const types = ['All', 'Chinese', 'Indian', 'Malay'];
	const typeColors = {
		Chinese: '#eab308',
		Malay: '#22c55e',
		Indian: '#f43f5e'
	};

	const radius = 6;

	// Create scales
	let x = 'carbs(g)';
	$: xAccessor = (d) => d[x];
	$: xScale = scaleLinear()
		.domain([0, max(data, xAccessor)])
		.range([0, width]);
	$: xGet = (d) => xScale(xAccessor(d));

	let y = 'fat(g)';
	$: yAccessor = (d) => d[y];
	$: yScale = scaleLinear()
		.domain([0, max(data, yAccessor)])
		.range([height, 0]);
	$: yGet = (d) => yScale(yAccessor(d));

	// Filter for selected type
	let processedData;
	$: if (selectedType != 'All') {
		processedData = data.filter((d) => d.type == selectedType);
	} else {
		processedData = data;
	}
</script>

<div class="title-container">
	<h1>Nutritional Content of Hawker Food</h1>
</div>

<!-- Inputs -->
<div class="inputs-container">
	<!-- Filter for type -->
	<select bind:value={selectedType}>
		{#each types as t}
			<option value={t}>{t}</option>
		{/each}
	</select>

	<!-- Select y variable -->
	<select bind:value={y}>
		{#each variables as v}
			<option value={v}>{v}</option>
		{/each}
	</select>

	<span>against</span>

	<!-- Select x variable -->
	<select bind:value={x}>
		{#each variables as v}
			<option value={v}>{v}</option>
		{/each}
	</select>
</div>

<!-- Chart -->
<div
	class="chart-container"
	bind:clientWidth={width}
	bind:clientHeight={height}
	on:mouseleave={() => (hoveredData = null)}
>
	<svg {width} {height}>
		<!-- Axes -->
		<line x1={0} y1={height} x2={width} y2={height} stroke={'#d6d3d1'} stroke-width={2} />
		<line x1={0} y1={height} x2={0} y2={0} stroke={'#d6d3d1'} stroke-width={2} />

		<text
			x={width}
			y={height}
			text-anchor={'end'}
			dominant-baseline={'hanging'}
			dy={10}
			fill={'#44403c'}
			>more {x} →
		</text>
		<text x={0} y={0} dy={-20} fill={'#44403c'}>↑ more {y} </text>

		<!-- Scatterplot -->
		{#each processedData as d (d.food)}
			<circle
				transition:fade={{ duration: 200 }}
				transform="translate({xGet(d)} {yGet(d)})"
				r={hoveredData == d ? radius * 2 : radius}
				fill-opacity={0.6}
				fill={typeColors[d.type]}
				stroke={'#78716c'}
				stroke-width={1.5}
				on:mouseover={() => {
					hoveredData = d;
				}}
			/>
		{/each}
	</svg>

	<!-- Tooltip -->
	{#if hoveredData}
		{#key hoveredData.food}
			<div
				class="tooltip"
				transition:fade={{ duration: 200 }}
				style:left={`${xGet(hoveredData)}px`}
				style:top={`${yGet(hoveredData)}px`}
			>
				{hoveredData.food.split('-')[0]}
			</div>
		{/key}
	{/if}
</div>

<style>
  .title-container {
    display: grid;
    place-content: center;
  }

	.chart-container {
		height: 450px;
		max-width: 800px;
		margin: 0 auto;
	}

	svg {
		overflow: visible;
	}

	text {
		font-size: 20px;
	}

	.inputs-container {
		display: flex;
		justify-content: center;
		gap: 12px;
		padding: 24px;
		margin-bottom: 48px;
		font-size: 20px;
		font-weight: 600;
	}

	.inputs-container select {
		font-size: 20px;
		font-weight: 600;
	}

	circle {
		transition: all 300ms;
	}

	.tooltip {
		position: absolute;
		pointer-events: none;
		padding: 8px 6px;
		background: white;
		box-shadow: rgba(0, 0, 0, 0.15) 2px 3px 8px;
		border-radius: 5px;
		font-size: 16px;
	}
</style>
