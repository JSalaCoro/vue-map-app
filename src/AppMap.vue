<template>
  <div id="app">
    <div class="cell cell-map">
      Map item
      <MapComponent/>
    </div>
    <div class="cell cell-edit">
      Edit
    </div>
    <div class="cell cell-inspect">
      Inspect
    </div>
  </div>
</template>

<script>
import MapComponent from './components/MapComponent.vue';

  export default {
    name: 'AppMap',
    components: {
      MapComponent
    }
  }
</script>

<style>
  html, body {
    height: 100%;
    margin: 0;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    height: 100%;
    width: 100%;
    display: grid;
    grid-template-columns: 100vh;
    grid-auto-rows: 1fr;
    grid-gap: 1rem;
    padding: 1rem;
    box-sizing: border-box;
  }

  .cell {
    border-radius: 4px;
    background-color: lightgrey;
  }

  .cell-map {
    grid-column: 1;
    grid-row-start: 1;
    grid-row-end: 3;
  }

  .cell-edit {
    grid-column: 2;
    grid-row: 1;
  }

  .cell-inspect {
    grid-column: 2;
    grid-row: 2;
  }
</style>

