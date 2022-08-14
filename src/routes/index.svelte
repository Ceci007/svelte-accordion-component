<script>
	import Item from '../components/item.svelte';
	const data = {
		foo: ['1 uno', '2 dos', '3 tres'],
		bar: ['4 cuatro', '5 cinco', '6 seis', '7 siete', '8 ocho', '9 nueve', '10 diez', '11 once'],
		baz: ['12 doce', '24 veinticuatro', '42 cuarenta y dos']
	};
</script>

<svelte:head>
	<title>Componente Acordeon</title>
</svelte:head>
<img src="/images/vegan-ice-cream.jpeg" class="image-background" />
{#each Object.entries(data) as entry}
	<Item {entry} />
{/each}

<style>
	* {
		margin: 0;
		padding: 0;
	}

	*,
	*:before,
	*:after {
		box-sizing: inherit;
	}

	html {
		box-sizing: border-box;
		font-size: 62.5%;
	}
	@media only screen and (max-width: 900px) {
		html {
			font-size: 50%;
		}
	}

	body {
		font-family: 'Open Sans', sans-serif;
		font-weight: 400;
		line-height: 1.6;
	}

	.image-background {
		position: fixed;
		width: 100%;
		height: 100vh;
		top: 0;
		left: 0;
		background-repeat: no-repeat;
		background-size: contain;
		background-position: center;
		object-fit: contain;
		z-index: -1;
	}

	@media only screen and (max-width: 600px) {
		.image-background {
			display: none;
		}
	}
</style>
