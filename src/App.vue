<template>
  <v-app id="inspire">
    <v-app-bar app color="yellow darken-1" flat>
      <v-app-bar-title min-width="10vh">
        <h1 class="font-weight-bold"><spam class="green--text text--darken-1">Fin</spam><spam class="light-blue--text text--darken-4">Vue</spam></h1>
      </v-app-bar-title>

      <v-tabs centered class="ml-n9" color="grey darken-1" v-model="tabsForm">
        <v-tab v-for="link in links" :key="link.key">
          {{ link.name }}
        </v-tab>
      </v-tabs>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row justify="center">
          <v-col cols="12" sm="8">
            <v-sheet min-height="80vh" rounded="lg">
              <HeaderList v-if="tabsForm !== 3" :valorTotal="valorTotal"/>
              <FormInsert v-if="tabsForm === 3" v-on:add-item-event="addNewItem"/>
              <Relationship v-if="tabsForm === 0" :dados="dados"/>
              <RelationshipGasto v-if="tabsForm === 1" :dados="dados"/>
              <PopSearche :dados="dados"/>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import FormInsert from "./components/FormInsert.vue"
import HeaderList from "./components/HeaderList.vue"
import Relationship from "./components/Relationship.vue"
import RelationshipGasto from "./components/RelationshipGasto.vue"
import PopSearche from "./components/PopSearche.vue"

export default {
  components: {
    FormInsert,
    HeaderList,
    Relationship,
    RelationshipGasto,
    PopSearche
  },
  data: () => ({
    tabsForm: 0,
    valorTotal: 0,
    links: [
      {
        name:"Tudo",
        key:"tudo"
      },
      {
        name:"Gastos",
        key:"gastos",
      },
      {
        name:"receitas",
        key:"receitas"
      },
      {
        name:"Inserir",
        key:"inserir"
      },
    ],
    dados: []
  }),
  methods: {
    addNewItem(newDado){
      this.dados = [...this.dados, newDado]
      this.valorTotal += newDado.value
    },
    calcValorTotal(dados){
      dados.forEach(d => {
        this.valorTotal += d.value
      })
    }
  },
  mounted() {
    if (localStorage.getItem("dados")){
      this.dados = JSON.parse(localStorage.getItem("dados"))
      this.calcValorTotal(this.dados)
    }
  },
  watch: {
  dados: {
    handler() {
      localStorage.setItem('dados',JSON.stringify(this.dados))
    },
    deep: true
  },
}

};
</script>