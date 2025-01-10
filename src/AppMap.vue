<template>
  <div id="app" >
    <div class="cell cell-map">
      <MapComponent/>
    </div>
    <div class="cell cell-edit">
      <LandingsPortChartComponent/>
    </div>
    <div class="cell cell-inspect">
      <LandingsYearlyChartComponent/>
    </div>
  </div>
</template>

<script>
import MapComponent from './components/MapComponent.vue';
import LandingsPortChartComponent from './components/LandingsPortChartComponent.vue';
import LandingsYearlyChartComponent from './components/LandingsYearlyChartComponent.vue';
  
export default {
    name: 'AppMap',
    components: {
      MapComponent,
      LandingsPortChartComponent,
      LandingsYearlyChartComponent
    }
  }

</script>

<style>
  html, body {
    height: 100%;
    margin: 0pxs;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    height: 100%;
    width: 50%;
    display: grid;
    grid-template-columns: 75vh 40vh 40vh ;
    grid-template-rows: 25vh 25vh 25vh;
    grid-auto-rows: 1fr;
    grid-gap: 1rem;
    padding: 1rem;
    box-sizing: border-box;
  }

  .cell {
    border-radius: 4px;
    background-color: rgb(255, 255, 255);
    border-style: solid;
    border-color: rgb(169, 171, 170);
    border-width: 1px;
  }

  .cell-map {
    grid-column: 1 ;
    grid-row: 1 / 4
  }

  .cell-edit {
    height: 100%;
    grid-column: 2 ;
    grid-row: 1 / 3;
  }

  .cell-inspect {
    height: 100%;
    grid-column: 2 / 4;
    grid-row: 3 ;
  }


</style>

