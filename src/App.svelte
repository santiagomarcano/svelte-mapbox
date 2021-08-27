<script>
  import Map from "./Map.svelte";
  import MapMarker from "./MapMarker.svelte";
  import Source from "./Source.svelte";
  import Layer from "./Layer.svelte";
  import datos from "./datos.js";
  import datos2 from "./datos2.js";
  import Popup from "./Popup.svelte";

  // console.log(JSON.stringify(datos2) === JSON.stringify(datos));

  let sourceName = "places";
  let sourceName2 = "places2";
</script>

<Map lat={38.907} lon={-77.04} zoom={14}>
  <Source {sourceName} {datos} />
  <Layer {sourceName} id={sourceName} />
  <Popup {sourceName} />

  <Source sourceName={sourceName2} datos={datos2} />
  <Layer sourceName={sourceName2} id={sourceName2} />
  <Popup sourceName={sourceName2} />

  <MapMarker lat={37.8225} lon={-122.0024} label="Svelte Body Shaping" />
  <MapMarker
    lat={33.8981}
    lon={-118.4169}
    label="Svelte Barbershop & Essentials"
  />
  <MapMarker lat={29.723} lon={-95.4189} label="Svelte Waxing Studio" />
  <MapMarker
    lat={28.3378}
    lon={-81.3966}
    label="Svelte 30 Nutritional Consultants"
  />
  <MapMarker lat={40.6483} lon={-74.0237} label="Svelte Brands LLC" />
  <MapMarker lat={40.6986} lon={-74.41} label="Svelte Medical Systems" />
</Map>
