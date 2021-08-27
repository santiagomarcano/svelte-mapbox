<script>
  import { getContext } from "svelte";
  import { mapbox, key } from "./mapbox.js";

  const { getMap } = getContext(key);
  const map = getMap();

  export let lat;
  export let lon;
  export let label;

  const popup = new mapbox.Popup({ offset: 25 }).setHTML(`<h1>${label}</h1>`);

  const marker = new mapbox.Marker()
    .setLngLat([lon, lat])
    .setPopup(popup)
    .addTo(map);
</script>
