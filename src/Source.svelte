<script>
  import { getContext } from "svelte";
  import { mapbox, key } from "./mapbox.js";

  export let datos;
  export let sourceName;

  const { getMap } = getContext(key);
  const map = getMap();

  map.on("load", () => {
    map.addSource(sourceName, {
      type: "geojson",
      data: datos,
    });
  });
</script>
