<script lang="ts">
	import { onMount } from 'svelte';
	import Chart from 'chart.js/auto';
	export let value = 0;
	export let backgroundColors = ['#36A2EB', '#E5E7EB']; // Customizable background colors
	export let textColor = '#B3E0FF'; // Customizable center text color
	let canvas: HTMLCanvasElement;
	let chart: Chart | undefined;

	onMount(() => {
		chart = new Chart(canvas, {
			type: 'doughnut',
			data: {
				labels: ['Active Users', 'Inactive Users'],
				datasets: [
					{
						data: [value, 100 - value],
						backgroundColor: backgroundColors, // Use prop
						borderWidth: 1,
						borderRadius: 10 // Rounded ends for the arc
					}
				]
			},
			options: {
				cutout: '82%', // Even thicker donut ring
				rotation: -135, // Start at top left
				circumference: 270, // Only 3/4 of a circle
				plugins: {
					legend: {
						display: false
					}
				},
				responsive: true,
				maintainAspectRatio: false
			}
		});
		return () => chart && chart.destroy();
	});

	$: if (chart) {
		chart.data.datasets[0].data = [value, 100 - value];
		chart.data.datasets[0].backgroundColor = backgroundColors; // Update if changed
		chart.update();
	}
</script>

<div class="relative flex h-40 w-40 flex-col">
	<canvas bind:this={canvas}></canvas>
	<div class="absolute inset-0 flex items-center justify-center">
		<span
			class="mt-4 text-[2.3rem] font-normal"
			style={`color: ${textColor}; letter-spacing: -1px; width: 60px; text-align: center;`}
		>
			{value}%
		</span>
	</div>
</div>
<!-- <div
	style="text-align: center; margin-top: 1.2rem; color: #C0C7D1; font-size: 0.98rem; font-family: 'Inter', 'Arial', sans-serif; font-weight: 300; letter-spacing: 0.01em;"
>
	Active Users Access Rate
</div> -->
