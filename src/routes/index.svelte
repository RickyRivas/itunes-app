<script>
	// goto will change the current route
	import { goto } from '$app/navigation';

	let searched = '';
	const search = () => {
		goto(`${searched}`);
	};
</script>

<section>
	<div class="container">
		<h1>Search An artist</h1>
		<form action="" on:submit|preventDefault={search}>
			<div class="location">
				<img src="/search.svg" alt="" width="25" height="25" />
			</div>
			<input type="search" bind:value={searched} placeholder="Search..." />
			<button disabled={searched == '' ? 'disabled' : ''}>Let's Go</button>
		</form>
	</div>
</section>

<style lang="scss">
	.container {
		padding: 1em;
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		/* Form elements */
		h1 {
			margin-bottom: 0.5em;
		}
		form {
			display: flex;
			justify-content: center;
			align-items: center;
			height: 2em;
			border-radius: 1em;
			position: relative;
			z-index: 2;
			width: 100%;
			max-width: 300px;
			box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
			background: white;
		}

		/* location  */
		form .location {
			height: 100%;
			display: flex;
			justify-content: center;
			align-items: center;
			padding: 0.5em;
			position: relative;
			border-radius: 1em 0 0 1em;
		}

		form .location img {
			width: 0.8em;
			height: 0.8em;
		}
		/* search bar */
		input[type='search'] {
			border: 0;
			height: 100%;
			padding: 1em 0;
			width: 100%;
			outline: none;
		}
		input[type='search']::placeholder {
			color: #222;
			font-size: 1em;
		}

		button {
			border: 0;
			height: 100%;
			width: 100%;
			cursor: pointer;
			border-radius: 0 1em 1em 0;
			background: #ff4b2b;
			color: white;
			width: 8em;
			padding: 0 0.5em 0 0.5em;
			transition: all 0.5s;
			&:disabled {
			}
		}
		button:hover {
			opacity: 0.9;
		}
	}
	input[type='search']::-webkit-search-decoration,
	input[type='search']::-webkit-search-cancel-button,
	input[type='search']::-webkit-search-results-button,
	input[type='search']::-webkit-search-results-decoration {
		-webkit-appearance: none;
	}
</style>
