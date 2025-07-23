<script lang="ts">
	import Card from '../components/card/card.svelte';
	import DonutChart from '../components/charts/DonutChart.svelte';
	const activeUsersAccessRate = 37;
	const resourcesUtilized = 67;
</script>

<div class="flex flex-col gap-4 md:flex-row">
	<div class="flex w-full flex-col gap-4 md:w-1/2 lg:flex-row">
		<div class="flex w-full grid-cols-2 flex-col gap-4 lg:grid">
			<div>
				<Card>
					<div class="flex justify-center">
						<DonutChart value={activeUsersAccessRate} />
					</div>
					<div class="flex justify-center text-center">
						<span class="max-w-24 text-gray-500">Active Users Access Rate</span>
					</div>
				</Card>
			</div>
			<div>
				<Card>
					<div class="flex justify-center">
						<DonutChart
							value={resourcesUtilized}
							backgroundColors={['orange', '#E5E7EB']}
							textColor="orange"
						/>
					</div>
					<div class="flex justify-center text-center">
						<span class="max-w-24 text-gray-500">Resources Utilized</span>
					</div>
				</Card>
			</div>

			<div class="col-span-2">
				<Card>
					Lorem ipsum dolor, sit amet consectetur adipisicing elit. Deleniti facilis, aliquid ipsam
					dolor porro ipsum, quisquam libero consectetur
				</Card>
			</div>
		</div>
	</div>

	<div class="flex w-full flex-col gap-4 md:w-1/2">
		<div>
			<Card>
				Lorem ipsum dolor, sit amet consectetur adipisicing elit. Deleniti facilis, aliquid ipsam
				dolor porro ipsum, quisquam libero consectetur
			</Card>
		</div>
		<Card>
			Lorem ipsum dolor, sit amet consectetur adipisicing elit. Deleniti facilis, aliquid ipsam
			dolor porro ipsum, quisquam libero consectetur
		</Card>
	</div>
</div>
