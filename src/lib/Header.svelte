<script>
	let navState = false;
	function toggleNav() {
		navState = !navState;
		window.document.body.classList.toggle('body-fixed');
	}
</script>

<header>
	<nav>
		<div class="navlinks-overlay {navState ? 'is-active' : ''}" on:click={toggleNav} />
		<ul class="nav-links {navState ? 'is-active' : ''}">
			<li class="nav-link active"><a href="/" on:click={toggleNav}>Home</a></li>
		</ul>
		<button
			on:click={toggleNav}
			class="hamburger {navState ? 'is-active' : ''} {navState ? 'fixed' : ''}"
			aria-label="Navigation Toggle"
		>
			<span class="hamburger-inner" />
		</button>
	</nav>
</header>

<style lang="scss">
	@media (min-width: 0px) {
		.hamburger {
			z-index: 10;
			position: relative;
			transition: all 0.5s;

			&::before {
				content: '';
				background-color: #f1f1f1;
				width: 50px;
				height: 50px;
				position: absolute;
				top: 50%;
				left: 50%;
				transform: translate(-50%, -50%);
				border-radius: 50%;
				transition: all 0.5s;
			}
		}

		header {
			position: relative;
			z-index: 10;
			width: 100vw;

			&.is-active {
				box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
				z-index: 10;
			}

			.hamburger.is-active {
				&::before {
					background-color: #393939;
				}
			}

			nav {
				position: absolute;
				display: flex;
				justify-content: flex-end;
				align-items: center;
				background-color: transparent;
				box-shadow: none;
				border: 0;
				padding: 1.2em;
				width: 100%;
				min-height: 75px;

				& p {
					color: black;
					font-size: 1.2em;
				}

				.logo-wrapper {
					position: absolute;
					left: 1rem;
					top: 1rem;
					display: flex;
					justify-content: center;
					align-items: center;
					width: 35%;
					max-width: 200px;

					img,
					svg {
						width: 100%;
						max-width: 100%;
						height: 100%;
						display: block;
						fill: transparent;
						position: relative;
					}
				}

				.nav-links {
					margin: 0;
					position: fixed;
					z-index: 100;
					right: 0px;
					height: 100vh;
					width: 80%;
					top: 0;
					display: flex;
					flex-direction: column;
					justify-content: center;
					align-items: flex-end;
					transform: translateX(100%);
					transition: all 0.3s ease-in-out;
					background-color: #18191a;
					list-style: none;
					padding: 2rem;

					& li {
						opacity: 1;
						padding: 0.5em 1em;
						text-align: center;
						font-weight: unset;
						display: flex;
						justify-content: center;
						align-items: center;
						font-size: 1.3em;
						position: relative;
						text-transform: uppercase;
						overflow: hidden;

						& a {
							color: #fff;
							text-decoration: none;
						}

						&::after {
							content: '';
							width: 100%;
							height: 2px;
							background-color: #0466c8;
							bottom: 0;
							position: absolute;
							transform: translateX(-101%);
						}

						&:hover {
							&::after {
								transition: transform 0.5s;
								transform: translate(0);
							}
						}

						&.active {
							&::after {
								transition: transform 0.5s;
								transform: translate(0);
							}
						}
					}

					& li:nth-child(1) {
						margin-top: -3em;
					}

					&.is-active {
						transform: translate(0%);
					}
				}

				.nav-btn {
					display: none;
					box-shadow: none;
				}
			}

			.navlinks-overlay {
				position: fixed;
				top: 0;
				left: 0;
				right: 0;
				width: 100vw;
				height: 100vh;
				transform: translateX(100%);
				background: rgba(0, 0, 0, 0.6);
				z-index: 99;

				&.is-active {
					transform: translate(0%);
					animation: fadeIn 0.3s ease-in;
				}
			}
		}

		@keyframes fadeIn {
			from {
				opacity: 0;
			}

			to {
				opacity: 1;
			}
		}
	}

	@media (min-width: 768px) {
		header {
			& nav {
				height: 10vh;
				padding: 0.5em;
				width: 100%;

				.nav-links {
					li {
						font-size: 1em;
					}
				}
			}
		}
	}

	@media (min-width: 1024px) {
		.hamburger {
			display: none !important;
			box-shadow: none;
		}

		header {
			z-index: 5;
			position: relative;
			display: flex;
			justify-content: center;
			align-items: center;
			height: 4rem;
			width: 100vw;
			background-color: #222;

			& .is-active {
				box-shadow: none;
				z-index: 100;
			}

			& nav {
				display: flex;
				justify-content: center;
				align-items: center;
				background-color: transparent;
				box-shadow: none;
				padding: 0 1em;
				width: 100%;
				height: 100%;
				max-width: 1200px;
				margin: auto;
				position: relative;

				.logo-wrapper {
					width: 16%;
					// max-width: 275px;
				}

				.nav-links {
					margin: 0;
					position: relative;
					right: unset;
					height: auto;
					top: unset;
					display: flex;
					flex-direction: row;
					justify-content: space-between;
					align-items: center;
					transform: unset;
					transition: unset;
					background-color: transparent;
					list-style: none;
					width: auto;

					& li {
						opacity: 1;
						padding: 0.5em;
						width: max-content;
						font-size: 0.75em;

						a {
							color: #fff;
						}
					}

					& li:nth-child(1) {
						margin-top: 0em;
					}
				}

				// .nav-btn {
				//   display: block;
				// }
			}

			.navlinks-overlay {
				display: none;
			}
		}
	}

	@media (min-width: 1200px) {
		header {
			z-index: 5;
			display: flex;
			justify-content: center;
			align-items: center;
			// height: 14rem;
			width: 100vw;

			& .is-active {
				z-index: 100;
			}

			& nav {
				justify-content: center;
				padding: 0;

				.logo-wrapper {
					position: relative;
					width: 45%;
				}

				.nav-links {
					display: grid;
					grid-template-columns: repeat(1, auto);
					grid-gap: 0.5rem;
					place-items: center;
				}

				.nav-btn {
					display: block;
					position: relative;
					display: flex;
					justify-content: center;
					align-items: center;

					img {
						width: 1.2rem;
						position: absolute;
						right: 0.5rem;
					}
				}
			}
		}
	}

	/* burger css */
	.hamburger {
		position: relative;
		width: 40px;
		height: 52px;
		cursor: pointer;
		z-index: inherit;
		background-color: transparent;
		border: 0;
		z-index: 9999;
		display: flex;
		justify-content: center;
		align-items: center;

		& .hamburger-inner {
			width: 40px;
			height: 2px;
			position: absolute;
			transition: all 0.3s ease-in-out;

			&::before,
			&::after {
				content: '';
				content: '';
				left: 0;
				position: absolute;
				width: 100%;
				height: 100%;
				background: #000;
				transition: all 0.3s ease-in-out;
			}

			&:before {
				transform: rotate(0deg) translate(0px, -4px);
			}

			&:after {
				transform: rotate(0deg) translate(0px, 4px);
			}
		}

		&.is-active {
			.hamburger-inner {
				&::before {
					transform: rotate(-45deg) translate(0px, 0px);
				}

				&::after {
					transform: rotate(45deg) translate(0px, 0px);
				}

				&::before,
				&::after {
					content: '';
					content: '';
					background: #fff;
				}
			}
		}
	}
</style>
