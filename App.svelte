<script>
  import Intro from "./Intro.svelte";

  let mouseX = window.innerWidth / 2;
  let mouseY = window.innerHeight / 2;
  let dx = 0;
  let dy = 0;
  let d = 0;
  let offset = 0;

  let bouncebackTimeout = 0;

  function handleMousemove(e) {
    dx = dx * 0.5 + Math.abs(e.screenX - mouseX);
    dy = dy * 0.5 + Math.abs(e.screenY - mouseY);
    mouseX = e.screenX;
    mouseY = e.screenY;

    d = Math.sqrt(dx * dx + dy * dy).toFixed(2);
    offset = Math.min(d * 0.3, 2); // too much if use offset d directly
    callBounceback(200);
  }

  function handleTouchmove(e) {
    dx = dx * 0.5 + Math.abs(e.touches[0].screenX - mouseX);
    dy = dy * 0.5 + Math.abs(e.touches[0].screenY - mouseY);
    mouseX = e.touches[0].screenX;
    mouseY = e.touches[0].screenY;

    d = Math.sqrt(dx * dx + dy * dy).toFixed(2);
    offset = Math.min(d * 0.3, 2); // too much if use offset d directly
    callBounceback(200);
  }

  function callBounceback(debounce) {
    window.clearTimeout(bouncebackTimeout);
    console.log(debounce);
    bouncebackTimeout = window.setTimeout(bounceback, debounce || 40);
  }

  function bounceback() {
    if (offset == 0) {
      return;
    }

    offset = offset < 1 ? 0 : +(offset * 0.8).toFixed(2);
    callBounceback();
  }
</script>

<svelte:window on:mousemove={handleMousemove} on:touchmove={handleTouchmove} />

<main>
  <div class="centering">
  	<Intro --text-color="#ee8855" --left="calc(-0.05em - {offset}px)" />
    <Intro --text-color="#22ddee" --left="calc(0.05em + {offset}px)" />
  </div>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Sans&display=swap");

  :global(body) {
    margin: 0;
    -webkit-font-smoothing: antialiased;
    background-color: #222;
    background-image: linear-gradient(#111, #222);
  }

  main {
    height: 100vh;
    font-family: "IBM Plex Sans", sans-serif;
  }

  .centering {
    position: relative;
    height: 100%;
    width: 100%;
    max-width: 800px;
    margin: 0 auto;
  }
</style>