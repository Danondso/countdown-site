<!-- Display the countdown timer in an element -->
<main>
    <h1>When Is Dublin Leaving?</h1>
    <p>{date}</p>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 100%;
    }
    h1 {
        font-size: 3rem;
    }
    p {
        font-size: 2rem;
    }
</style>
<script>
// Set the date we're counting down to
const countDownDate = new Date("Mar 18, 2022 17:00:00").getTime();
let date = '';

// Update the count down every 1 second
const x = setInterval(function() {
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
  if (distance < 0) {
    clearInterval(x);
    date = "HE GONE!";
  }
}, 10);
</script>
