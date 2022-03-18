<script>
	// Set the date we're counting down to
	const countDownDate = new Date('Mar 18, 2022 17:00:00').getTime();
	let showIframe = false;
	let date = '';
	let message = '';

	// Update the count down every 1 second
	const countDown = setInterval(function () {
		// Get today's date and time
		const now = new Date().getTime();

		// Find the distance between now and the count down date
		const distance = countDownDate - now;

		// Time calculations for days, hours, minutes and seconds
		const days = Math.floor(distance / (1000 * 60 * 60 * 24));
		const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
		const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
		const seconds = Math.floor((distance % (1000 * 60)) / 1000);

		// Display the result in the element with id="demo"
		date = `${days}d ${hours}h ${minutes}m ${seconds}s`;

		// If the count down is finished, write some text
		if (days <= 4 && days > 3) {
			message = 'Four Days Remain.';
		} else if (days <= 3 && days > 2) {
			message = 'Three Days Remain.';
		} else if (days <= 2 && days > 1) {
			message = 'He probably had his exit interview...';
		} else if (days <= 1 && days > 0) {
			message = 'The penultimate day.';
		} else if (days <= 0) {
			message = 'Dawn of the final day.';
			showIframe = true;
		}
		if (days <= 0) {
			clearInterval(countDown);
			date = 'HE GONE!';
			message = '';
			showIframe = true;
		}
	}, 10);
</script>

<!-- Display the countdown timer in an element -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Fredoka&display=swap" rel="stylesheet" />

<main>
	<h1>When Is Dublin Leaving?</h1>
	<p>{date}</p>
	<p>{message}</p>
	{#if showIframe}
		<iframe
			class="iframe"
			src="https://www.youtube.com/embed/tiJzCahaN8w?autoplay=1"
			title="Fake Your Death - My Chemical Romance"
			frameborder="0"
			allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
			allowfullscreen
		/>
	{/if}
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		text-align: center;
		font-family: Fredoka;
		padding: 2%;
		position: absolute;
		top: 50%;
		left: 25%;
		word-wrap: break-word;
		width: 50vw;
		border: 2px solid black;
		border-radius: 10px;

		transform: translateY(-50%);
		box-shadow: 10px 10px 20px #aaaaaa;
	}

	h1 {
		font-size: 3rem 3rem 20%;
	}
	p {
		font-size: 2rem;
	}

	.iframe {
		width: 400px;
		height: 400px;
	}

	@media only screen and (max-height: 420px) {
		main {
			border: none;
			box-shadow: none;
		}

		h1 {
			font-size: 1rem 1rem 20%;
		}
		p {
			font-size: 1rem;
		}

		.iframe {
			width: 150px;
			height: 150px;
		}
	}

	@media only screen and (max-width: 715px) {
		main {
			border: none;
			box-shadow: none;
		}

		.iframe {
			width: 300px;
			height: 300px;
		}
	}
</style>
