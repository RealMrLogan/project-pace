<script lang="ts">
	export let onClick: () => void;
	export let position: 'left' | 'right';

	const leftStyles: string =
		'border-r-2 border-b-2 active:border-r-0 active:border-b-0 active:border-l-2 active:border-t-2';
	const rightStyles: string =
		'border-l-2 border-t-2 active:border-l-0 active:border-t-0 active:border-r-2 active:border-b-2';
</script>

<button
	class={`p-4 text-xl text-slate-800 border-slate-800 rounded-lg ${position === 'left' ? leftStyles : rightStyles}`}
	on:click={onClick}><slot /></button
>
