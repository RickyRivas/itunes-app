<script>
	import { goto } from '$app/navigation';
	// this is a default route
	import { page } from '$app/stores';
	import { onMount } from 'svelte';

	let songResults = [];

	onMount(async () => {
		let searched = $page.params.searched;

		const itunesSearched = await fetch(
			`https://itunes.apple.com/search?term=${searched}&entity=song`
		);

		let response = await itunesSearched.json();

		songResults = response.results;

		console.log(songResults);
	});
</script>

<section>
	<div class="items">
		{#each songResults as result}
			{#if result.trackName.length <= 50}
				<div class="songItem">
					<img src={result.artworkUrl100} alt="" width="100" height="100" />
					<div class="info">
						<p>{result.trackName}</p>
						<button on:click={goto(`${$page.params.searched}/${result.trackId}`)}>View More</button>
					</div>
				</div>
			{/if}
		{/each}
	</div>
</section>

<style lang="scss">
	.items {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-wrap: wrap;
		grid-gap: 1em;
		width: 100%;
		max-width: 1200px;
		margin: auto;
	}
	.songItem {
		display: flex;

		width: 14em;
		position: relative;
		box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
		transition: all 0.5s;
		border-radius: 0.5em;
		img {
			width: 5em;
			height: 5em;
			border-bottom-left-radius: 0.5em;
			border-top-left-radius: 0.5em;
		}
		.info {
			display: flex;
			justify-content: space-between;
			align-items: flex-start;
			flex-direction: column;
			padding: 0.5em;
			p {
				font-size: 0.7em;
				margin-bottom: 0.5em;
			}
			button {
				border: 0;
				width: 7em;
				padding: 0.5em;
				background: linear-gradient(#ff416c, #ff4b2b);
				color: white;
				font-size: 0.5em;
			}
		}
	}
</style>
