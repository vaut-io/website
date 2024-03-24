<script>
	import { Bar, Pie } from 'svelte-chartjs';
	import 'chart.js/auto';
	import { rnpq, hcpairs } from './data.js';

	// import { Chart, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';
	// Chart.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);
	// import { ArcElement } from 'chart.js';

	// Chart.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

	let rnpqPieCharts = [];

	let hcpairsBarCharts = [];

	rnpq.forEach((a) => {
		rnpqPieCharts.push({
			labels: ['Respuesta correcta', 'Respuesta incorrecta'],
			statement: a.statement,
			datasets: [
				{
					label: 'Último curso',
					data: [a.correctLastYear, 42 - a.correctLastYear],
					backgroundColor: [
						'hsl(120, 80%, 20%, 0.3)',
						'hsl(0, 80%, 80%, 0.3)',
					],
					borderWidth: 2,
					borderColor: [
						'hsl(120, 80%, 20%, 0.5)',
						'hsl(0, 80%, 80%, 0.5)',
					]
				},
				{
					label: 'Primer curso',
					data: [a.correctFirstYear, 92 - a.correctFirstYear],
					backgroundColor: [
						'hsl(120, 80%, 20%, 0.3)',
						'hsl(0, 80%, 80%, 0.3)',
					],
					borderWidth: 2,
					borderColor: [
						'hsl(120, 80%, 20%, 0.5)',
						'hsl(0, 80%, 80%, 0.5)',
					]
				},
			]
		});
	});

	hcpairs.forEach((a) => {
		hcpairsBarCharts.push({
			labels: ['1', '2', '3', '4', '5', '6', '7'],
			statement: a.statement,
			datasets: [
				{
					label: 'Primer curso',
					data: a.firstYear.map(count => (count / 96)),
					backgroundColor: getBackgroundColors(a),
					borderWidth: 2,
					borderColor: getBorderColors(a),
				},
				{
					label: 'Último curso',
					data: a.lastYear.map(count => (count / 42)),
					backgroundColor: getBackgroundColors(a),
					borderWidth: 2,
					borderColor: getBorderColors(a),
				},
			],
		});
	});

	function getBackgroundColors(a) {
		if (a.inverted) return ([
			'hsl(0, 80%, 80%, 0.5)',
			'hsl(20, 70%, 70%, 0.5)',
			'hsl(40, 60%, 60%, 0.5)',
			'hsl(60, 50%, 50%, 0.5)',
			'hsl(80, 60%, 40%, 0.5)',
			'hsl(100, 70%, 30%, 0.5)',
			'hsl(120, 80%, 20%, 0.5)',
		]);
		return ([
			'hsl(120, 80%, 20%, 0.5)',
			'hsl(100, 70%, 30%, 0.5)',
			'hsl(80, 60%, 40%, 0.5)',
			'hsl(60, 50%, 50%, 0.5)',
			'hsl(40, 60%, 60%, 0.5)',
			'hsl(20, 70%, 70%, 0.5)',
			'hsl(0, 80%, 80%, 0.5)',
		]);
	}

	function getBorderColors(a) {
		if (a.inverted) return ([
			'hsl(0, 80%, 80%, 1)',
			'hsl(20, 70%, 70%, 1)',
			'hsl(40, 60%, 60%, 1)',
			'hsl(60, 50%, 50%, 1)',
			'hsl(80, 60%, 40%, 1)',
			'hsl(100, 70%, 30%, 1)',
			'hsl(120, 80%, 20%, 1)',
		]);
		return ([
			'hsl(120, 80%, 20%, 1)',
			'hsl(100, 70%, 30%, 1)',
			'hsl(80, 60%, 40%, 1)',
			'hsl(60, 50%, 50%, 1)',
			'hsl(40, 60%, 60%, 1)',
			'hsl(20, 70%, 70%, 1)',
			'hsl(0, 80%, 80%, 1)',
		]);
	}
</script>

<main class="gutter">
	<section class="pt-2xl-3xl">
		<hgroup class="flex flex-col gap-[1em]">
			<h1>Datos visualizados</h1>
			<p>Esta página web corresponde al estudio, <i>"Conocimiento del dolor y actitudes hacia el dolor crónico entre estudiantes universitarios de fisioterapia: análisis preliminar de un estudio observacional"</i>.</p>
			<p>En cada gráfico, verde (claro) = mejor, rojo (oscuro) = peor. Pulsa una etiqueta arriba del gráfico para mostrar y esconder los grupos. Coloca el puntero o aprieta sobre una parte del gráfico para ver la frecuencia absoluta o relativa de respuestas.</p>
		</hgroup>
	</section>
	<section class="flex flex-col gap-l-xl pt-2xl-3xl">
		<h2>RNPQ: conocimiento sobre el dolor</h2>
		<ul class="flex flex-col gap-xl-2xl">
			{#each rnpqPieCharts as chart}
				<li class="flex flex-wrap flex-row-reverse justify-end items-center gap-y-2xs-xs">
					<div class="basis-[0] grow-[999] min-w-[50%]">
						<h3 class="text-0 font-normal font-base tracking-base text-pretty">{chart.statement}</h3>
					</div>
					<div class="basis-[20ch]">
						<div class="max-w-[20ch]">
							<Pie data={chart} options={{ responsive: true }} />
						</div>
					</div>
				</li>
			{/each}
		</ul>
	</section>
	<section class="flex flex-col gap-l-xl py-2xl-3xl">
		<h2>HC-PAIRS: actitudes hacia el dolor crónico</h2>
		<ul class="flex flex-col gap-xl-2xl">
			{#each hcpairsBarCharts as chart}
				<li class="flex flex-wrap flex-row-reverse justify-end items-center gap-y-xs-s gap-x-xs-s">
					<div class="basis-[0] grow-[999] min-w-[25%]">
						<h3 class="text-0 font-normal font-base tracking-base">{chart.statement}</h3>
					</div>
					<div class="basis-[35ch]">
						<Bar data={chart} options={{ responsive: true }} />
					</div>
				</li>
			{/each}
		</ul>
	</section>
</main>
