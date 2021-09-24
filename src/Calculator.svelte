<script>
    import Buttons from "./Buttons.svelte";
    import Header from "./Header.svelte";
    import Display from "./Display.svelte";
    import {inputValue, outputValue} from "./store";
    import {evaluate} from "mathjs";


</script>

<div class="calculator">
    <Header/>
    <Display on:equalsAction={() => outputValue.set(evaluate($inputValue.replace('√', 'sqrt')))}/>
    <Buttons/>
</div>

<style>
    .calculator {
        width: 380px;
        margin: 0 auto;
        border-radius: 25px;
        overflow: hidden;
        background-color: #fff;
        box-shadow: 0 15px 15px 0 rgba(0, 0, 0, .25)
    }
</style>
