<template>
  <div class="card">
    <h3>{{ name }} - {{ code }} </h3>
    <addres>
      <strong>Endereço: {{ address }}</strong>
      <p>Cidade: {{ city }}</p>
      <p>Área total: {{ area }} m²</p>
    </addres>
  </div>
</template>

<script>
export default {
  name: 'Warehouse',
  props: {
    id: Number,
    name: String,
    code: String,
    address: String,
    city: String,
    area: Number
  }
}
</script>

<style>
.card {
  border-style: solid;
  border-radius: 25px;
  margin-bottom: 10px;
  width: 30%;
  margin-left: auto;
  margin-right: auto;
}
</style>