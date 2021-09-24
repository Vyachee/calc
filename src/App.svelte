<script>
	import Calculator from "./Calculator.svelte";
</script>

<svelte:head>
	<style>
		* {
			padding: 0;
			margin: 0;
			box-sizing: border-box;
			font-family: 'Roboto', sans-serif;
			user-select: none;
		}
	</style>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;700&display=swap" rel="stylesheet">
</svelte:head>

<div class="wrap">
	<Calculator/>
</div>

<style>
	.wrap {
		width: 100%;
		height: 100%;
		background-color: #F5F5F5;
		display: flex;
		align-items: center;
		justify-content: center;
	}
</style>
