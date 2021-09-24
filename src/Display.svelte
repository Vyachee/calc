<script>
	import {inputValue, outputValue} from "./store";
	import {createEventDispatcher} from 'svelte';


	const dispatch = createEventDispatcher();
	const onKeyPress = e => {
		if (e.charCode === 13) {
			dispatch('equalsAction');
		}
	};

</script>

<div class="display">
	<input type="text" on:keypress={onKeyPress} bind:value={$inputValue} class="data-input">
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
