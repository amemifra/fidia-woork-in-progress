<script>
  import WorkInProgress from './WorkInProgress.svelte';
  import { fade, fly, draw } from 'svelte/transition';
	import { onMount } from 'svelte';

  let visible = false;
  onMount(() => {
    visible = true;
  });
</script>

<style>
	.app {
    display: grid;
    grid-template-rows: 2.5rem calc(100% - 2.5rem);
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    overflow: hidden;
	}

	.h1 {
    grid-row: 1 / 1;
    color: var(--second-color);
    padding: 0 1.5rem;
    margin: 0;
    display: flex;
    align-items: center;
  }
  .wip {
    grid-row: 2 / 2;
    padding: 2rem 1.5rem;
  }
</style>
<div class="app">

  {#if visible}
  <div class="h1">
    {#each 'FIDIΛ' as char, i}
      <span
        in:fade="{{delay: 200 + i * 150, duration: 800}}"
      >{char}</span>
    {/each}
  </div>
  {/if}
  <div class="wip">
    <WorkInProgress />
  </div>
</div>
