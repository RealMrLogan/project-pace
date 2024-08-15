<script lang="ts">
	import { Button } from '$lib';

	const MIN_ESTIMATE: number = 0.5;

	let minValue: number = 0;
	const handleMinInput = (event: Event) => {
		const input = event.target as HTMLInputElement;
		if (parseFloat(input.value) < 0) {
			input.value = '0';
		}
		minValue = parseFloat(input.value);
	};

	let maxValue: number = 8;
	const handleMaxInput = (event: Event) => {
		const input = event.target as HTMLInputElement;
		if (parseFloat(input.value) < minValue) {
			input.value = minValue.toString();
		}
		maxValue = parseFloat(input.value);
	};

	const MAX_ESTIMATE: number = maxValue - MIN_ESTIMATE;

	$: estimate = (minValue + maxValue) / 2;
	console.log({ estimate });

	const onLess = () => {
		const newEstimate = (estimate - minValue) / 2;
		if (newEstimate < MIN_ESTIMATE) return;
		estimate = newEstimate;
	};
	const onMore = () => {
		const newEstimate = (estimate + maxValue) / 2;
		if (newEstimate > MAX_ESTIMATE) return;
		estimate = newEstimate;
	};

	// TODO: handle dynamic scaling
	// - right now it can only go one way; it cannot go + then -
</script>

<section class="grid place-content-center pt-12">
	<div class="flex flex-col items-center text-violet-100 font-bold">
		<h1>
			<span class="text-5xl ml-4 text-slate-800">project</span><br />
			<em class="text-9xl block -mt-16 opacity-50">pace</em>
		</h1>
	</div>

	<div class="mt-48" />
	<div class="grid gap-8 grid-rows-2 grid-cols-3 justify-items-center">
		<label class="flex flex-col"
			>days<input
				type="number"
				class="w-20 text-2xl bg-transparent border-2 border-slate-200 rounded-lg"
				bind:value={minValue}
				on:input={handleMinInput}
			/>
			{minValue * 8} hours
		</label>
		<div />
		<label class="flex flex-col"
			>days<input
				type="number"
				class="w-20 text-2xl bg-transparent border-2 border-slate-200 rounded-lg"
				bind:value={maxValue}
				on:input={handleMaxInput}
			/>
			{maxValue * 8} hours
		</label>

		<Button onClick={onLess} position="left">Less</Button>
		<div>
			<p class="text-5xl text-slate-800 min-w-32">{estimate}</p>
			days
		</div>
		<Button onClick={onMore} position="right">More</Button>
	</div>
</section>
