<style>
  .intro {
    position: absolute;
    top: 50%;
    color: var(--text-color);
    padding: 20px 30px 30px;
    border: 3px solid var(--text-color);
    border-radius: 3px;
    mix-blend-mode: screen;
    transform: translate(var(--left), -50%);
    box-sizing: border-box;
    transition: transform 30ms ease;
  }

  @media (max-width: 450px), (max-width: 800px) and (max-aspect-ratio: 7/9) {
    .intro {
      top: 0;
      transform: translate(var(--left));
    }
  }

  h1,
  h2 {
    display: inline;
    font-size: 52px;
    font-weight: normal;
    letter-spacing: 0;
  }

  @media (max-width: 540px) {
    h1,
    h2 {
      font-size: 40px;
    }
  }

  h1 {
    margin-top: 0;
  }

  h2::before {
    content: "\00a0";
  }

  a {
    color: var(--text-color);
    text-decoration: none;
    border-bottom: 3px solid var(--text-color);
  }
</style>

<div class="intro">
	<h1>Freddie Sze</h1>
	<h2>is a supposed web developer who is too busy with non web-dev work to update his own website. If you’d like to, you can see his <a href="http://cargocollective.com/fdsze">old website.</a></h2>
</div>