<script>
	import {inputValue, outputValue} from "./store";
</script>

<div class="display">
	<input type="text" bind:value={$inputValue} class="data-input">
	{#if $outputValue !== ''}
		<div class="output-display">
			<span class="equals">=</span>
			<span class="data-output" contenteditable="true">{$outputValue}</span>
		</div>

	{/if}
</div>

<style>

	.display {
		width: 100%;
		min-height: 150px;
		position: relative;
		padding: 10px;
	}

	.output-display {
		position: absolute;
		right: 10px;
		bottom: 10px;
	}

	.data-input {
		font-size: 18px;
		width: 100%;
	}

	.data-output {
		display: inline-block;
		font-size: 24px;
	}

	.data-output {
		font-weight: bold;
	}


	input {
		border: none;
		outline: none;
	}
</style>
