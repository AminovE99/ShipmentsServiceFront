<template>
  <div>
    <table>
      <thead>
      <tr>
        <th>Delete</th>
        <th>Id</th>
        <th>Created at</th>
        <th>Delivered at</th>
        <th>Departure address</th>
        <th>Destination address</th>
        <th>Status</th>
      </tr>
      </thead>
      <ShipmentItem
          v-for="shipment of shipments"
          v-bind:shipment="shipment" :key="shipment.id"
      />
    </table>
  </div>
</template>
<script>
import ShipmentItem from "@/components/ShipmentItem";

export default {
  props: ['shipments'],
  components: {
    ShipmentItem
  }
}
</script>

<style scoped>
table {
  width: 100%;
  margin-bottom: 20px;
  border: 1px solid #dddddd;
  border-collapse: collapse;
}

th {
  font-weight: bold;
  padding: 5px;
  background: #efefef;
  border: 1px solid #dddddd;
}

td {
  border: 1px solid #dddddd;
  padding: 5px;
}
</style>