<script>
  import { getContext } from "svelte";
  import { mapbox, key } from "./mapbox.js";

  export let sourceName;

  const { getMap } = getContext(key);
  const map = getMap();

  map.on("load", () => {
    map.on("click", sourceName, (e) => {
      console.log(e.features);
      // Copy coordinates array.
      const coordinates = e.features[0].geometry.coordinates.slice();
      const description = e.features[0].properties.description;

      console.log(e.features[0].properties);
      // Ensure that if the map is zoomed out such that multiple
      // copies of the feature are visible, the popup appears
      // over the copy being pointed to.
      // while (Math.abs(e.lngLat.lng - coordinates[0]) > 180) {
      //     coordinates[0] += e.lngLat.lng > coordinates[0] ? 360 : -360;
      // }

      new mapbox.Popup().setLngLat(coordinates).setHTML(description).addTo(map);
    });

    // Change the cursor to a pointer when the mouse is over the places layer.
    map.on("mouseenter", "places", () => {
      map.getCanvas().style.cursor = "pointer";
    });

    // Change it back to a pointer when it leaves.
    map.on("mouseleave", "places", () => {
      map.getCanvas().style.cursor = "";
    });
  });
</script>
