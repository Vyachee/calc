<script>

    import {evaluate} from "mathjs";

    const buttons = [
        1, 2, 3, '*', 'C',
        4, 5, 6, '/', '^',
        7, 8, 9, '+', '√',
        '(', 0, ')', '-', '='
    ];

    let inputValue = '';
    let outputValue = '';

    function enterValue(value) {
        if (value === 'C') {
            inputValue = '';
            outputValue = '';
        } else if (value === '=') {
            outputValue = evaluate(inputValue);
        } else {
            inputValue += value;
        }
    }
</script>

<div class="calculator">
    <div class="header">
        <span class="title">Calculator 3000</span>
    </div>

    <div class="display">
        <input type="text" bind:value={inputValue} class="data-input">
        {#if outputValue !== ''}
            <div class="output-display">
                <span class="equals">=</span>
                <span class="data-output" contenteditable="true">{outputValue}</span>
            </div>

        {/if}
    </div>

    <div class="buttons">
        {#each buttons as b}
            <div class="button" on:click={() => enterValue(b)}>
                <span class="value">{b}</span>
            </div>
        {/each}
    </div>

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


    .calculator {
        width: 380px;
        margin: 0 auto;
        border-radius: 25px;
        overflow: hidden;
        background-color: #fff;
        box-shadow: 0 15px 15px 0 rgba(0, 0, 0, .25)
    }

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

    .header {
        background-color: #434343;
        color: #fff;
        padding: 2px 2px 2px 20px;
        font-size: 14px;
    }

    input {
        border: none;
        outline: none;
    }

    .data-output {
        font-weight: bold;
    }

</style>
