<template>
  <div>
    <h1>Galpões Cadastrados</h1>

    <input class="busca" type="text" placeholder="Buscar galpão" v-model="query">

    <div v-for="w in filterWarehouse" :key="w.id">
      <Warehouse
        :name     = "w.name"
        :id       = "w.id"
        :code     = "w.code"
        :address  = "w.address"
        :city     = "w.city"
        :area     = "w.area"
      />
    </div>
  </div>
</template>

<script>
import Warehouse from '../components/Warehouse.vue'

export default {
  name: 'WarehouseList',
  components: {
    Warehouse
  },

  data(){
    return{
      warehouses:[],
      query: ""
    }
  },

  async mounted(){
    this.getWarehouses()
  },

  methods: {
    async getWarehouses(){

      // Realizando a requisição
      const response = await this.$http.get('http://localhost:3000/api/v1/warehouses');

      const result = await response.json();

      // Exibindo os dados no console do navegador
      console.log(result);

      // Adicionando dados de result no array warehouses
      this.warehouses = result;

      return this.warehouses

    }
  },

  computed:{
    filterWarehouse(){
      return this.warehouses.filter(warehouse => {
        return warehouse.name.toLowerCase().includes(this.query.toLowerCase());
      })
    }
  }
}
</script>


<style>
.busca {
  margin-bottom: 20px;
}
</style>