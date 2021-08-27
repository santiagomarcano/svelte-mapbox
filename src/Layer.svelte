<script>
  import { getContext } from "svelte";
  import { mapbox, key } from "./mapbox.js";

  export let id;
  export let sourceName;

  const { getMap } = getContext(key);
  const map = getMap();

  map.on("load", () => {
    map.addLayer({
      id: id,
      type: "symbol",
      source: sourceName,
      layout: {
        "icon-image": `{icon}`,
        "icon-allow-overlap": true,
      },
    });
  });
</script>
