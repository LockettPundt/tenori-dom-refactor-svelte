<script>
  import SingleNote from './SingleNote.svelte';
  export let note;
  export let steps;
  export let frequency;
</script>

<style>
  div {
    display: grid;
    gap: 3px;
    grid-template-columns: repeat(16, minmax(0, auto));
  }
</style>

<div>
  {#each steps as step, i}
    <SingleNote {step} {note} {frequency} stepNumber={i + 1} />
  {/each}
</div>
