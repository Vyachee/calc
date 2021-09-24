<script>
	import {inputValue, outputValue} from "./store";
	import {evaluate} from "mathjs";

	const buttons = [
		1, 2, 3, '*', 'C',
		4, 5, 6, '/', '^',
		7, 8, 9, '+', '√',
		'(', 0, ')', '-', '='
	];

	function enterValue(value) {
		if (value === 'C') {
			inputValue.set('');
			outputValue.set('');
		} else if (value === '√') {
			inputValue.update(v => v + '√(');
		} else if (value === '=') {
			try {
				outputValue.set(evaluate($inputValue.replace('√', 'sqrt')));
			}	catch (e) {
				outputValue.set('ERROR!')
			}
		} else {
			inputValue.update(v => v + value);
		}
	}
</script>


<div class="buttons">
	{#each buttons as b}
		<div class="button" on:click={() => enterValue(b)}>
			<span class="value">{b}</span>
		</div>
	{/each}
</div>

<style>
	.buttons {
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		gap: 1px;
	}

	.button {
		background-color: #434343;
		color: #fff;
		height: 0;
		width: 100%;
		padding-bottom: 100%;
		position: relative;
		cursor: pointer;
		font-size: 25px;
	}

	.button:hover {
		background-color: #2D2D2D;
	}

	.button .value {
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		width: 100%;
		height: 100%;
	}
</style>
