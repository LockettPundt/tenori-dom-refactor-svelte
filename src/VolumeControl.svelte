<script>
  import { tenoriState } from './stores';

  const volumeChange = (num) => {
    return tenoriState.update((store) => {
      const updatedStore = { ...store };
      if (num > 0) {
        updatedStore.volume += 0.1;
      } else if (updatedStore.volume <= 0) {
        updatedStore.volume = 0;
      } else {
        updatedStore.volume -= 0.1;
      }
      return updatedStore;
    });
  };
</script>

<div>
  <button on:click={() => volumeChange(0)}> <i class="fas fa-minus" /> </button>
  <i class="fas fa-volume-up" />
  <button on:click={() => volumeChange(1)}> <i class="fas fa-plus" /> </button>
</div>

<style>
  div {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    justify-items: center;
  }
  button {
    border: none;
    appearance: none;
    background-color: inherit;
    outline: none;
    cursor: pointer;
  }
</style>
