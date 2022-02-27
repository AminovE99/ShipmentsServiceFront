<template>
  <tr>
    <button v-on:click="deleteShipment(shipment.id)">Delete</button>
    <td>{{ shipment.id }}</td>
    <td>{{ shipment.created_at }}</td>
    <td>{{ shipment.delivered_at }}</td>
    <td>{{ shipment.departure_address }}</td>
    <td>{{ shipment.destination_address }}</td>
    <td>
      <select>
        <option selected>{{ shipment.status }}</option>
        <option>Draft</option>
        <option>IN PENDING</option>
        <option>DELIVERED</option>
      </select></td>
  </tr>
</template>
<script>

export default {
  props: {
    shipment: {
      type: Object,
      required: true
    }
  },
  methods: {
    deleteShipment(id) {
      console.log(id);
      fetch(`http://localhost:8000/api/shipment/${id}/`, {
        method: "DELETE",
        headers: {'Content-Type': 'application/json'}
      })
    }
  }
}
</script>