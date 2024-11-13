<script>
	import ClickableTile from './ClickableTile.svelte';
	let color_name = $state('red');
	let background_color = $state('red');
	let colors = $state(['red', 'orange', 'yellow']);

	function AddColor() {
		if (CSS.supports("color", $state.snapshot(color_name))) {
			colors.push( $state.snapshot(color_name));
		}
	}
</script>

<div style="background-color: {background_color}">
	{#each colors as color}
		<ClickableTile 
			style="background-color: {color};
						 width: {100 / colors.length}%"
			onclick={() => background_color = color}
			/>
	{/each}
</div>


<textarea bind:value={color_name}></textarea>
<br>
<button onclick={AddColor}>Add Color</button>
<button onclick={() => colors.pop()}>Remove Color</button>

<style>
	div {
		height: 50%
		
	}
</style>

	
