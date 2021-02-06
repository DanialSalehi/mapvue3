<template>
  <div class="home red" id="imap">
    <mapir
      id="map-main"
      :center="center"
      height="500"
      width="700"
      :apiKey="apiKey"
      @click="setLocation"
    >
      <mapMarker
        :coordinates="center"
        color="red"
        @click="showMsg = !showMsg"
        :draggable="true"
      />
      <div style="position: absolute; left: 47.5%; top:47%">
        <h1>1sfdd</h1>
      </div>
    </mapir>

    <map />
    <br />
    <br />
    <br />
    <h1 @click="addNewLocation">Add Location</h1>
    <br />
    <h1>{{ center }}</h1>
  </div>
</template>
<script>
import { mapir, mapMarker } from "mapir-vue";

export default {
  name: "Home",
  components: {
    mapir,
    mapMarker,
  },
  created() {},

  data() {
    return {
      c: [48.684844, 31.384496],
      apiKey:
        "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImY0Y2IyNTQ3YzlmODZhYjU4MTM0MTAzYTAyZjMzNzJiNGVmMzg5MmY5ZmQ0ZmQ4ZTI5MDkxN2ViMmU3YWYwYmJhY2NiZjcxYTMwODIyZjY5In0.eyJhdWQiOiIxMjQyOSIsImp0aSI6ImY0Y2IyNTQ3YzlmODZhYjU4MTM0MTAzYTAyZjMzNzJiNGVmMzg5MmY5ZmQ0ZmQ4ZTI5MDkxN2ViMmU3YWYwYmJhY2NiZjcxYTMwODIyZjY5IiwiaWF0IjoxNjExMjA1OTQxLCJuYmYiOjE2MTEyMDU5NDEsImV4cCI6MTYxMzcxMTU0MSwic3ViIjoiIiwic2NvcGVzIjpbImJhc2ljIl19.mPr3eehV7SAQ1ZeFx-wSWwV9xM_gNgs_OV0ODXNy8ddcFxgMm-gsxhOTxbz3vdi093Mc54Pq644prg1nrE_dhfqPjkTyr3-izGvc0LDZZehcgAIb4BvQ6lFWJgfLGs5qofQDiJAvEowm1mD9U54J2yEh9K5s7O4cc3vVbChFXdeekcyCNA_-3v3T0_zOmvJbNnIMkOotPRIUIVtxmf3BzLvrtC467lv5tFd-AGiSjAHl1HWPzLQSnWcCcuMlURSkExOlyvFlKWoNtVXu6t66zYmbe_g_Z2OaBkEj8Aal309QBUedzG32nE8kj2-RDquV8QODMYejpMXtC9wgpq2Jbw",
      center: [48.684844, 31.354496],
      z: 3,
      pikdLocation: [51.420296, 35.732379],
      Markers: this.$store.state.Markers,
      showMsg: false,
      newMsg: "",
    };
  },
  methods: {
    setLocation(e) {
      this.pikdLocation = [e.actualEvent.lngLat.lng, e.actualEvent.lngLat.lat];
      console.log("480|130");
    },
    addNewLocation() {
      this.$store.state.Markers.push({
        coordinates: [this.center.lng, this.center.lat],
        msg: this.newMsg,
        colore: "blue",
        z: this.z,
      });
      console.log(this.center);
    },
    hh(e) {
      console.log(e);
    },
  },
};
</script>

<style>
#imap {
  width: 700px;
  height: 500px;
}
</style>
