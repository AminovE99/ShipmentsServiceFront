<template>
  <div id="app">
    <h1>Shipments service</h1>
    <AddShipment @add-shipment="addShipment"/>
    <ShipmentTable v-bind:shipments="shipments"
    />
  </div>
</template>

<script>
import ShipmentTable from '@/components/ShipmentTable'
import AddShipment from "@/components/AddShipment";

export default {
  name: 'App',
  data() {
    return {
      shipments: [
        {'id': 1}
      ]
    }
  },
  mounted() {
    fetch('http://localhost:8000/api/shipment/').then(response => response.json())
        .then(shipments => {
          this.shipments = shipments
        })
  },
  components: {
    ShipmentTable, AddShipment
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
