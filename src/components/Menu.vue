<template>
  <v-container>
    <v-row>
      <v-col>
        <v-toolbar>
          <v-toolbar-title>WarehouseApp</v-toolbar-title>
          <v-spacer></v-spacer>
          <nav>
            <v-btn text to="/">Home</v-btn>
            <v-btn text to="/warehouses">Galpões Cadastrados</v-btn>
            <v-btn text to="/new_warehouse">Cadastrar Galpão</v-btn>
            <v-btn text to="/about">Sobre</v-btn>
          </nav>
        </v-toolbar>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'Menu'
}
</script>

<style>

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

</style>