<script>
	import { Bar, Pie } from 'svelte-chartjs';
	import 'chart.js/auto';
	import { rnpq, hcpairs } from './data.js';

	// import { Chart, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';
	// Chart.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);
	// import { ArcElement } from 'chart.js';

	// Chart.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

	let rnpqPieCharts = []

	let hcpairsBarCharts = [];

	rnpq.forEach((a, i) => {
		rnpqPieCharts.push({
			labels: ['Correcto', 'Incorrecto / No Sé'],
			statement: a.statement,
			datasets: [
				{
					label: 'Último curso',
					data: [a.correctLastYear, 42 - a.correctLastYear],
					backgroundColor: [
						'rgba(155, 234,159,0.4)',
						'rgba(255, 134,159,0.4)',
					],
					borderWidth: 2,
					borderColor: [
						'rgba(155, 234,159,0.4)',
						'rgba(255, 134,159,0.4)',
					]
				},
				{
					label: 'Primer curso',
					data: [a.correctFirstYear, 92 - a.correctFirstYear],
					backgroundColor: [
						'rgba(155, 234,159,0.4)',
						'rgba(255, 134,159,0.4)',
					],
					borderWidth: 2,
					borderColor: [
						'rgba(155, 234,159, 1)',
						'rgba(255, 134, 159, 1)',
					]
				},
			]
		});
	});

	hcpairs.forEach((a, i) => {
		hcpairsBarCharts.push({
			labels: ['1', '2', '3', '4', '5', '6', '7'],
			statement: a.statement,
			datasets: [
				{
					label: 'Primer curso',
					data: a.firstYear,
					backgroundColor: [
						'rgba(255, 134,159,0.4)',
					],
					borderWidth: 2,
					borderColor: [
						'rgba(255, 134, 159, 1)',
					]
				},
				{
					label: 'Último curso',
					data: a.lastYear,
					backgroundColor: [
						'rgba(255, 177, 101,0.4)'
					],
					borderWidth: 2,
					borderColor: [
						'rgba(255, 177, 101, 1)'
					]
				}
			]
		});
	});
</script>

<main class="gutter">
	<section class="py-2xl-3xl">
		<hgroup class="flex flex-col gap-[1em]">
			<h1>Data visualization!</h1>
			<p>Click on the labels at the top of each chart to show only first or last year students. Hover or press on a data item to see more information</p>
		</hgroup>
	</section>
	<section class="flex flex-col gap-l-xl py-2xl-3xl">
		<hgroup class="flex flex-col gap-[1em]">
			<h2>RNPQ</h2>
			<p>V = verdadero / F = falso</p>
		</hgroup>
		<ul class="flex flex-col gap-xl-2xl">
			{#each rnpqPieCharts as chart, i}
				<li class="flex flex-wrap items-center gap-y-3xs-2xs gap-x-l-xl">
					<div class="basis-[0] grow-[999] min-w-[50%]">
						<p>{i + 1}. {chart.statement}</p>
					</div>
					<div class="basis-[25ch]">
						<Pie data={chart} options={{ responsive: true }} />
					</div>
				</li>
			{/each}
		</ul>
	</section>
	<ul class="flex flex-col gap-l-xl py-2xl-3xl">
		<hgroup class="flex flex-col gap-[1em]">
			<h2>HC-PAIRS</h2>
		</hgroup>
		{#each hcpairsBarCharts as chart}
			<li class="flex flex-col gap-xs-s">
				<p>{chart.statement}</p>
				<Bar data={chart} options={{ responsive: true }} />
			</li>
		{/each}
	</ul>
</main>

<style>
	.chart-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(min(20ch, 100%), 1fr));
		gap: var(--spacing-l-xl);
	}
</style>
