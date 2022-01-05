<script context="module">
	export const prerender = true;
</script>

<script>

	import Counter from '$lib/Counter.svelte';
	import { onMount } from 'svelte';
	import { web3, defaultChainStore, makeContractStore } from 'svelte-web3';

	// No "exports" main defined in C:\Users\AJ\Desktop\Blockchain\Tutorials\svelte-contracts-test\node_modules\svelte-web3\package.json 
	// imported from C:\Users\AJ\Desktop\Blockchain\Tutorials\svelte-contracts-test\node_modules\svelte-contracts\dist\index.js
	import { createContract } from 'svelte-contracts';

	import ERC20ABI from '$lib/ERC20ABI.json';

	// Uncaught (in promise) Error: [svelte-web3] Cannot find Web3
	/*
		at init (stores.js:40)
		at set1193Provider (stores.js:68)
		at setProvider (stores.js:89)
		at Proxy.setBrowserProvider (stores.js:113)
		at index.svelte? [sm]:19
		at run (index.mjs:18)
		at Array.map (<anonymous>)
		at index.mjs:1749
		at flush (index.mjs:1057)
		at init (index.mjs:1841)
	*/

	onMount(() => {
		defaultChainStore.setBrowserProvider();
		const SHIB = makeContractStore(ERC20ABI, '0x95ad61b0a150d79219dcf64e1e6cc01f0b64c4ce');
	});

</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<section>
	<h1>
		<div class="welcome">
			<picture>
				<source srcset="svelte-welcome.webp" type="image/webp" />
				<img src="svelte-welcome.png" alt="Welcome" />
			</picture>
		</div>

		to your new<br />SvelteKit app
	</h1>

	<h2>
		try editing <strong>src/routes/index.svelte</strong>
	</h2>

	<Counter />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
