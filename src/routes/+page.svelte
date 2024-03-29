<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import { Slider } from '$lib/components/ui/slider/index.js';

	let distance = [0];
	let speed = 90;
	let time = 0;
</script>

<div class="mx-auto min-h-screen max-w-7xl px-4 sm:px-6 lg:px-8">
	<!-- We've used 3xl here, but feel free to try other max-widths based on your needs -->
	<div class="mx-auto max-w-5xl">
		<!-- Content goes here -->
		<div class="overflow-hidden rounded-lg bg-white shadow">
			<div class="grid grid-cols-1 gap-6 bg-red-500 px-4 py-5 sm:p-8 md:grid-cols-3 md:gap-12">
				<!-- Content goes here -->
				<Card.Root>
					<Card.Header>
						<Card.Title>Distance</Card.Title>
						<Card.Description>The estimated distance to fly in miles</Card.Description>
					</Card.Header>
					<Card.Content>
						<p>{distance}</p>
					</Card.Content>
					<Card.Footer>
						<Slider bind:value={distance} max={40} step={1} class="max-w-[70%]" />
					</Card.Footer>
				</Card.Root>
				<Card.Root>
					<Card.Header>
						<Card.Title>Speed</Card.Title>
						<Card.Description>The aircrafts speed</Card.Description>
					</Card.Header>
					<Card.Content>
						<p>Card Content</p>
					</Card.Content>
					<Card.Footer>
						<p>Card Footer</p>
					</Card.Footer>
				</Card.Root>
				<Card.Root>
					<Card.Header>
						<Card.Title>Time</Card.Title>
						<Card.Description>The estimated time to fly in minutes</Card.Description>
					</Card.Header>
					<Card.Content>
						<p>Card Content</p>
					</Card.Content>
					<Card.Footer>
						<p>Card Footer</p>
					</Card.Footer>
				</Card.Root>
			</div>
		</div>
	</div>
</div>
