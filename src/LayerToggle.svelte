<script>
  import { getContext } from "svelte";
  import { key } from "./mapbox.js";

  export let sourceName;
  let visibility = true;

  const { getMap } = getContext(key);

  const toggleVisibility = () => {
    const map = getMap();
    const state = map.getLayoutProperty(sourceName, "visibility");
    if (state === "visible") {
      map.setLayoutProperty(sourceName, "visibility", "none");
      visibility = false;
    } else {
      map.setLayoutProperty(sourceName, "visibility", "visible");
      visibility = true;
    }
  };
</script>

<div
  on:click={toggleVisibility}
  class="toggler"
  class:visible={visibility}
>
  {sourceName}
</div>

<style>
  .toggler {
    position: absolute;
    top: 5px;
    right: 5px;
    background: white;
    padding: 15px;
    border-radius: 5px;
    cursor: pointer;
  }
  .visible {
    background: red;
  }
</style>
