<script>
  import { fade, draw } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';
  
  import { onMount } from 'svelte';
  
  let pnts = [0, 200, 250, 200, 250, 100, 175, 100, 175, 150];
  let width = 0;
  $: xOffset = width / 2 - 175

  $: points = pnts.map((p, i) => i % 2 ? p : p + xOffset).reduce((a, c) => a + ' ' + c.toString(), '');

  let points = '0 200 250 200 250 100 175 100 175 150';
  let visible = false;
  onMount(() => {
    visible = true;
  });
</script>


<svelte:window bind:innerWidth={width}/>

{#if visible}
<svg>
  <polyline {points}
    stroke="var(--second-color-4)" 
    fill="transparent" 
    stroke-width="5" 
    in:draw="{{duration: 1000, delay: 400, easing: quintOut}}"/>
</svg>

<div class="centered">
  {#each 'WORK IN PROGRESS' as char, i}
    <span
      in:fade="{{delay: 1000 + i * 150, duration: 800}}"
    >{char}</span>
  {/each}
</div>
{/if}


<style>

	svg {
		width: 100%;
		height: 100%;
  }

  polyline {
    opacity: 0.2;
  }

  
	.centered {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%,-50%);
		letter-spacing: 0.12rem;
		color: #676778;
		font-weight: 100;
	}
  

</style>