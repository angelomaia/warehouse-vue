<template>
  <div>
    <h1 class="mb-6">Galpões Cadastrados</h1>

    <v-card>
      <v-card-text>
        <v-text-field type="text" placeholder="Buscar galpão" v-model="query"></v-text-field>
        <WarehouseTable :warehouses="filterWarehouse"/>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
import Warehouse from '../components/Warehouse.vue'
import WarehouseTable from '../components/WarehouseTable.vue'

export default {
  name: 'WarehouseList',
  components: {
    Warehouse,
    WarehouseTable
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
</style>