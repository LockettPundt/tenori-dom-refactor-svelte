<script>
  import Memory from './Memory.svelte';
  import NoteGrid from './NoteGrid.svelte';
  import StartStop from './StartStop';
  import Controls from './Controls.svelte';
  import { initClient } from '@urql/svelte';

  const dev = import.meta.env.NODE_ENV === 'development';
  const url = dev ? 'http://localhost:3000' : 'https://tenori-api.herokuapp.com/';

  initClient({
    url,
  });
</script>

<div class="App">
  <Memory />
  <StartStop />
  <NoteGrid />
  <Controls />
</div>

<style>
  :global(body) {
    margin: 0;
    font-family: 'Apercu', Helvetica, sans-serif;
    background-color: rgb(28, 28, 28);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-content: center;
    width: 100vw;
    height: 100vh;
    background-image: url('./compBook.png');

    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
  }
  :global(html) {
    line-height: 1.15;
    color: #43414e;
  }

  :global(*) {
    box-sizing: border-box;
  }

  @font-face {
    font-family: 'Apercu';
    font-style: normal;
    font-weight: 500;
    src: url('./apercu_regular-webfont.woff');
  }
  .App {
    display: grid;
    gap: 10px;
    margin: auto;
    background-color: white;
    width: 80%;
    max-width: 800px;
    padding: 5px;
    border-radius: 3px;
    font-size: 1.3em;
  }
  :global(button) {
    transition: 0.28s ease-in-out;
  }

  :global(button:hover) {
    color: rgb(120, 120, 120);
    transform: scale(1.4, 1.4);
    transition: 0.2s ease-in-out;
  }

  @media (max-width: 767px) {
    .App {
      width: 100%;
      font-size: 1em;
    }
  }

  @media (max-width: 375px) {
    .App {
      width: unset;
      font-size: 1em;
      padding: unset;
      gap: 10px;
    }
  }

  @media (max-width: 321px) {
    .App {
      height: 100vh;
    }
  }
</style>
