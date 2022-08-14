<script>
	import { slide } from 'svelte/transition';
	export let entry;
	let isOpen = false;
	const toggle = () => (isOpen = !isOpen);
</script>

<div class="container">
	<button on:click={toggle} aria-expanded={isOpen}>
		<div class="icon-box">
			<svg
				style="tran"
				width="20"
				height="20"
				fill="none"
				stroke-linecap="round"
				stroke-linejoin="round"
				stroke-width="2"
				viewBox="0 0 24 24"
				stroke="currentColor"><path d="M9 5l7 7-7 7" /></svg
			>
		</div>
		{entry[0]}
	</button>
	{#if isOpen}
		<ul transition:slide={{ duration: 300 }}>
			{#each entry[1] as item}
				<li><span>#</span> {item}</li>
			{/each}
		</ul>
	{/if}
</div>

<style>
	.container {
		width: 500px;
		margin: 0 auto;
		margin-top: 40px;
	}

	@media only screen and (max-width: 600px) {
		.container {
			width: 300px;
		}
	}

	button {
		border: none;
		background: #6495ed;
		width: 100%;
		display: flex;
		align-items: center;
		text-align: left;
		color: inherit;
		font-size: 26px;
		cursor: pointer;
		margin: 0;
		padding: 0.5em 1em;
		border-bottom: 6px solid #87cefa;
		color: #fff;
		border-top-left-radius: 10px;
		border-top-right-radius: 10px;
	}

	button:focus {
		outline: none;
	}

	.icon-box {
		width: 40px;
		height: 40px;
		background: #87cefa;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-right: 20px;
		border-radius: 50%;
	}

	svg {
		transition: transform 0.2s ease-in;
		color: #fff;
	}

	[aria-expanded='true'] svg {
		transform: rotate(0.25turn);
	}

	ul {
		background: #fff;
		box-shadow: 0 2rem 5rem rgba(0, 0, 0, 0.2);
		padding: 0.5em 1em;
		list-style: none;
		border-radius: 10px;
	}

	li {
		padding: 0.5em 1em;
		font-weight: bold;
		color: rgba(0, 0, 0, 0.4);
	}

	li span {
		color: #6495ed;
	}
</style>
