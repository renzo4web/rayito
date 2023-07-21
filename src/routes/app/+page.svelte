<script lang="ts">
	import { requestProvider } from 'webln';
	import { onMount } from 'svelte';

	let ask = '';
	let walletIsConnected = false;
	$: console.log(ask);

	const connectToProvider = () => {
		requestProvider()
			.then(async (webln) => {
				walletIsConnected = webln?.enabled;
				const walletInfo = await webln?.getInfo();
				console.log({ walletInfo });
			})
			.catch((err) => {
				console.log(err);
			});
	};
</script>

<div class="flex flex-col justify-center items-center">
	<h1 class="md:text-5xl text-2xl text-center font-bold">Awesome pages</h1>
	<input
		type="text"
		placeholder="Ask!!"
		class="input mt-10 input-bordered input-primary w-full max-w-xs"
		bind:value={ask}
	/>
	{#if walletIsConnected}
		<h3>Wallet connected</h3>
	{:else}
		<button on:click={connectToProvider} class="btn btn-primary mt-10">Connect Wallet</button>
	{/if}
</div>
