<script>
	// Set the date we're counting down to
	const countDownDate = new Date('Mar 18, 2022 17:00:00').getTime();
	let showIframe = false;
  let generateImages = false;
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
		}
		if (distance < 0) {
			clearInterval(countDown);
			date = 'HE GONE!';
			message = '';
			showIframe = true;
      generateImages = true;
		}
	}, 10);

  const rootPath = '../../';
  const fileNames = [
    'static/grimace-dance.gif',
    // 'static/2cfd287697d00b60.png',
    // 'static/3da55e899389a724.png',
    // 'static/3fbdc99088e276eb.gif',
    // 'static/4cc2fe105525c298.png',
    // 'static/4d153b5dd573d83c.png',
    // 'static/6e671af588287030.png',
    // 'static/7cb1e80aa1b1566e.jpeg',
    // 'static/9f0d1a5057e11a6c.png',
    // 'static/56c611c39b6ce6e8.gif',
    // 'static/74d675d75edb4f40.png',
    // 'static/242b8176c333956f.png',
    // 'static/653ce31f8e7de8b3.png',
    // 'static/676b26bbed04d951.gif',
    // 'static/02252d789c989c2f.png',
    // 'static/6640e857780857f1.png',
    // 'static/7402bae9acf28b60.png',
    // 'static/41169bf4f99b4954.png',
    // 'static/9925666badbf0957.png',
    // 'static/a19eee8d9d516c93.png',
    // 'static/ac2b2bbfbd43da20.png',
    // 'static/ae3fd7fb053aa0ca.png',
    // 'static/b80118d1a542faa9.png',
    // 'static/ba32a2331373be41.png',
    // 'static/c386069b56c2d09e.png',
    // 'static/cedc9220d38489fa.png',
    // 'static/cfbcc480c9501efb.png',
    // 'static/d0a77d03b7c91c56.png',
    // 'static/dd7cf8158ce45b12.png',
    // 'static/e352b8b1e77d0afd.gif',
    // 'static/e8778b391c8d6d4f.png',
    // 'static/ec7aed54a96065c3.png',
    // 'static/ef70f8c7500880e7.png',
    // 'static/f90078da92c4533f.png',
    // 'static/f31140892c11917e.png'
  ];
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

  {#if generateImages}
    {#each fileNames as fileName}
      <div 
          class="flier" 
          style:position="absolute"          
          style:top=0
          style:left=0
      >
        <img src={`${rootPath}${fileName}`} alt="That Flies Around" />
      </div>
    {/each}
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

  .flier {
	pointer-events: none;
}

.flier > * {
/* Adjust animation duration to change the element’s speed */
  animation: fly 50s linear infinite;
  pointer-events: none !important;
	transform: translateX(-120%) translateY(-120%) rotateZ(0);
	position: fixed;
	z-index: 999999;
}

 /* Keyframe values control where the element will begin
    and end its trajectory across the screen. Each rule
    represents a path the element follows across the screen. */


@keyframes fly {

	98.001%, 0% {
    display: block;
		transform: translateX(-200%) translateY(100vh) rotateZ(0deg)
	}

	15% {
		transform: translateX(100vw) translateY(-100%) rotateZ(180deg)
	}

	15.001%, 18% {
		transform: translateX(100vw) translateY(-30%) rotateZ(0deg)
	}

	40% {
		transform: translateX(-200%) translateY(3vh) rotateZ(-180deg)
	}

	40.001%, 43% {
		transform: translateX(-200%) translateY(-100%) rotateZ(-180deg)
	}

	65% {
		transform: translateX(100vw) translateY(50vh) rotateZ(0deg)
	}

	65.001%, 68% {
		transform: translateX(20vw) translateY(-200%) rotateZ(180deg)
	}

	95% {
		transform: translateX(10vw) translateY(100vh) rotateZ(0deg)
	}
}
</style>
