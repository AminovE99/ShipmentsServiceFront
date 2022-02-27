<template>
  <form @submit="onSubmit">
    <label for="departure_address">Departure address: </label>
    <input id="departure_address" type="text" name="departure_address" v-model="departureAddress">
    <div>
      <label for="destination_address">Destination address: </label>
      <input id="destination_address" type="text" name="destination_address" v-model="destinationAddress">
    </div>
    <div>
      <label for="status">Status: </label>
      <select id="status" name="status" v-model="status">
        <option value="OPEN">OPEN</option>
        <option value="DRAFT">DRAFT</option>
        <option value="IN PENDING">IN PENDING</option>
        <option value="DELIVERED">DELIVERED</option>
      </select>
    </div>
    <button type="submit">Save</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      destinationAddress: '',
      departureAddress: '',
      status: ''
    }
  },
  methods: {
    onSubmit() {
      const newShipment = {
        'departure_address': this.departureAddress,
        'destination_address': this.destinationAddress,
        'status': this.status,
      }
      fetch('http://localhost:8000/api/shipment/', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify(newShipment)
      })
    }
  },
  name: "AddShipment"
}
</script>

<style scoped>

</style>