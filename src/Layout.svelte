<script>
  import { mobile } from "./components/store.js";
  let w;
  let y;

  $: if (w < 768) {
    mobile.set(true);
  } else {
    mobile.set(false);
  };

</script>

<style>
  canvas {
    position: absolute;
  }
  #large-header {
    width: 100%;
  }
</style>

<svelte:head>
  <script
    src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/499416/TweenLite.min.js">

  </script>
  <script
    src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/499416/EasePack.min.js">

  </script>
  <script src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/499416/demo.js">

  </script>
</svelte:head>

<svelte:window bind:innerWidth={w}/>
<div id="large-header">
  {#if !$mobile}
    <canvas id="demo-canvas" />
  {/if}
  <slot />
</div>
