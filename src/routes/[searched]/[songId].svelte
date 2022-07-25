<script context="module">
	// triggers before onmount
	export async function load({ fetch, params }) {
		let songId = params.songId;

		const url = `https://itunes.apple.com/search?term=${songId}&entity=song`;

		let response = await fetch(url);

		return {
			status: response.status,
			props: {
				data: response.ok && (await response.json())
			}
		};
	}
</script>

<script>
	export let data;
	const song = data.results[0];
</script>

<section>
	<div class="item">
		<img src={song.artworkUrl100} alt="" />
		<h3>{song.trackName}</h3>
		<audio controls src={song.previewUrl}>
			Your browser does not support the
			<code>audio</code> element.
		</audio>
	</div>
</section>

<style lang="scss">
	section {
		padding: 1em;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.item {
		box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
		background: white;
		border-radius: 0.5em;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		padding: 1em;
		img {
			margin-bottom: 1em;
		}
		h2 {
			margin-bottom: 0.5em;
		}
	}
</style>
