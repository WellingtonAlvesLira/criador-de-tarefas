<template>
<v-container>
  <v-data-table
    :headers="headers"
    :items="desserts"
    class="elevation-1"
  >
    <template v-slot:top>
    <v-toolbar flat>
        <v-toolbar-title >LISTA DE TAREFAS</v-toolbar-title>
        <v-divider class="mx-5" inset vertical></v-divider>
        <v-spacer></v-spacer>
      </v-toolbar>
    </template>
    <template v-slot:[`item.actions`]="{ item }">
        <i @click="editTarefa(item.id)" class="fa fa-pencil-square-o fa-2x d-block ma-1"></i>
        <i @click.prevent=deleteTarefa(item.id) class="fa fa-trash-o fa-2x ma-1"></i>
    </template>
  </v-data-table>
  </v-container>
</template>

<script>

import API from "@/api/api.js";

  export default {
    name: 'listaTarefa',
    mixins:[API],
     data: () => ({
    dialog: false,
    headers: [
      {
        text: "Id",
        align: "start",
        sortable: false,
        value: "id",
      },
      { text: "Nome", value: "nome" },
      { text: "Nom da Tarefa", value: "nomeTarefa" },
      { text: "Hora", value: "hora" },
      { text: "Descrição", value: "descricao" },
      { text: "AÇÕES", value: "actions", sortable: false },
    ],
    desserts: [],
  }),

   created() {
    //listando pedidos que foram realizados pelo usuário.
    this.listarTarefa();
  },
  methods: {
    listarTarefa() {
      this.get("/tarefas").then((resposta) => {
        this.desserts = resposta.data;
      });
    },

    editTarefa(id){
      alert(id)
    },

   deleteTarefa(itemId) {
          this.delete(`/tarefas/${itemId}`).then((resposta) => {
          if (resposta.data){
            alert('Tem certeza ?')
             this.listarTarefa();
          }
        });
    },

  }
  }
</script>

<style scoped>
</style>