<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import { Slider } from '$lib/components/ui/slider/index.js';
	import { Button } from '$lib/components/ui/button';

	function calculateTime(distance: number, speed: number): number {
		// convert knots to mph
		speed = speed * 1.15;
		let hours = distance / speed;
		let minutes = hours * 60;
		return Math.round(minutes);
	}

	let distance = [0];
	let max_distance = 40;
	let step_distance = 1;
	let speed = [90];
	let min_speed = 80;
	let max_speed = 400;
	let step_speed = 10;
	$: time = calculateTime(distance[0], speed[0]);
</script>

<div class="mx-auto min-h-screen max-w-7xl px-4 sm:px-6 lg:px-8">
	<!-- We've used 3xl here, but feel free to try other max-widths based on your needs -->
	<div class="mx-auto grid h-screen max-w-5xl grid-cols-1 place-content-center">
		<!-- Content goes here -->
		<div class="overflow-hidden rounded-lg shadow">
			<div class="grid grid-cols-1 gap-2 p-4 sm:p-6 md:grid-cols-2 md:gap-6">
				<Card.Root class="col-span-1 md:col-span-2">
					<Card.Header
						><Card.Title>Estimated time</Card.Title><Card.Description
							>The estimated time to fly in minutes</Card.Description
						></Card.Header
					>
					<Card.Content>
						<p>{time}</p>
					</Card.Content>
				</Card.Root>
				<!-- Content goes here -->
				<Card.Root>
					<Card.Header>
						<Card.Title>Distance</Card.Title>
						<Card.Description>The distance to fly in miles</Card.Description>
					</Card.Header>
					<Card.Content>
						<p>{distance}</p>
					</Card.Content>
					<Card.Footer>
						<Slider bind:value={distance} max={max_distance} step={step_distance} class="w-full" />
					</Card.Footer>
				</Card.Root>
				<Card.Root>
					<Card.Header>
						<Card.Title>Speed</Card.Title>
						<Card.Description>The aircrafts speed in kts</Card.Description>
					</Card.Header>
					<Card.Content>
						<p>{speed}</p>
					</Card.Content>
					<Card.Footer class="flex w-full flex-col space-y-8">
						<div class="w-full">
							<Slider
								bind:value={speed}
								min={min_speed}
								max={max_speed}
								step={step_speed}
								class="w-full"
							/>
						</div>
						<div class="flex w-full space-x-2">
							<Button variant="default" on:click={() => (speed = [90])}>90</Button>
							<Button variant="default" on:click={() => (speed = [120])}>120</Button>
							<Button variant="default" on:click={() => (speed = [150])}>150</Button>
							<Button variant="default" on:click={() => (speed = [180])}>180</Button>
							<Button variant="default" on:click={() => (speed = [210])}>210</Button>
						</div>
					</Card.Footer>
				</Card.Root>
			</div>
		</div>
	</div>
</div>
