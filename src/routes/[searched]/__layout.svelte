<script>
	import { goto } from '$app/navigation';
	// nested layout
	const goBack = () => {
		window.history.back();
	};
</script>

<div class="subheader">
	<button class="back" on:click={goBack}
		><img src="/turn-back.svg" alt="" width="10" height="10" /></button
	>
	<button
		on:click={() => {
			goto('/');
		}}>New Search</button
	>
</div>

<slot />

<style lang="scss">
	.subheader {
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		margin-bottom: 1em;
	}
	button {
		border: none;
		padding: 0.5em;
		margin: 0 0.5em;
	}
	.back {
		border-radius: 50%;
		width: 2em;
		height: 2em;
		display: flex;
		justify-content: center;
		align-items: center;
		background: #ff4b2b;
		img {
			filter: invert(1);
		}
	}
</style>
