<h1>aha</h1>
<!-- <div id='map' style='width: 400px; height: 300px;'></div> -->
<div id='map' style='width: 100vmax; height: 100vmax;'></div>
<script>
  import maplibregl from 'maplibre-gl';
  import 'maplibre-gl/dist/maplibre-gl.css';
  import { onMount } from 'svelte';
  const { Marker } = maplibregl

  let marker;

  // maplibregl references `document` variable which is available on browser mount.
  onMount(() => {
    let map = new maplibregl.Map({
      container: 'map', style: 'https://demotiles.maplibre.org/style.json',
      center: [0, 0],
      zoom: 1
    })
    // let marker = new Marker({
    marker = new Marker({
      // color: "#000000",
        color: "#FFFFFF",
        draggable: true
      })
      .setLngLat([106.82, -6.19])
      .addTo(map);
    // dragend: https://maplibre.org/maplibre-gl-js/docs/examples/drag-a-marker
    marker.on('dragend', markerDragend);
  });
  function markerDragend(/* marker */) {
    let lngLat = marker.getLngLat();
    // fetch lngLat...
    console.log({ lngLat })
  }
</script>
