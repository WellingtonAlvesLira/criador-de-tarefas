<template>
  <v-container>
    <v-row justify="center">
      <v-col id="form" cols="12" md="6">
        <img
          id="img-form"
          src="https://us.123rf.com/450wm/opicobello/opicobello1509/opicobello150900066/45315691-ilustraci%C3%B3n-de-un-l%C3%A1piz-de-color-marr%C3%B3n-dibujar-un-gancho.jpg?ver=6"
          alt=""
        />
        <v-text-field v-model="data_tarefa.nome" label="Seu Nome" outlined>
        </v-text-field>
        <v-text-field
          v-model="data_tarefa.nomeTarefa"
          label="Nome da Tarefa"
          outlined
        ></v-text-field>
        <v-text-field
          v-model="data_tarefa.hora"
          label="Hora"
          value="12:30:00"
          type="time"
        ></v-text-field>
        <v-textarea
          height="60"
          v-model="data_tarefa.descricao"
          label="Descrição da Tarefa"
          placeholder="Detalhes"
        ></v-textarea>
        <v-btn text id="btn" @click="salvar_tarefa"> Salvar </v-btn>
        <v-btn text id="btnLimpar" @click="limpar_tarefa"> Limpar </v-btn>
        <span id="showSucesso1" dense text v-show="menssage1">
          {{ menssage1 }}
        </span>
        <span id="showError2" dense text v-show="menssage2">
          {{ menssage2 }}
        </span>
      </v-col>
    </v-row>
  </v-container>
</template>


<script>
import API from "@/api/api.js";
export default {
  name: "formTarefas",
  mixins: [API],
  data() {
    return {
      data_tarefa: {
        nome: "",
        nomeTarefa: "",
        hora: "",
        descricao: "",
      },
      menssage1: "",
      menssage2: "",
    };
  },
  methods: {
    salvar_tarefa() {
      if (
        this.data_tarefa.nome == "" ||
        this.data_tarefa.nomeTarefa == "" ||
        this.data_tarefa.hora == "" ||
        this.data_tarefa.descricao == ""
      ) {
        this.showMenssageErro();
      } else
        this.post("/tarefas/", this.data_tarefa).then((resposta) => {
          if (resposta.data) {
            this.showMenssageSucess();
            this.limpar_tarefa();
          }
        });
    },
    showMenssageSucess() {
      this.menssage1 = `Tarefa ${this.data_tarefa.nomeTarefa} salva com sucesso`;
      setTimeout(() => (this.menssage1 = ""), 6000);
    },
    showMenssageErro() {
      this.menssage2 = `Por favor. Preencher todos os campos...`;
      setTimeout(() => (this.menssage2 = ""), 6000);
    },
    limpar_tarefa() {
      this.data_tarefa.nome = "";
      this.data_tarefa.nomeTarefa = "";
      this.data_tarefa.hora = "";
      this.data_tarefa.descricao = "";
    },
  },
};
</script>

<style scoped>
#form {
  margin: auto;
  padding: 15px;
  background: white;
  box-shadow: 10px 10px 8px 5px rgb(37, 5, 5);
}
#btn {
  background: rgb(98, 180, 98);
  color: white;
  margin-right: 5px;
}
#btn:hover {
  background: rgb(72, 224, 72);
  color: white;
  margin-right: 5px;
}
#btnLimpar {
  background: rgb(207, 60, 60);
  color: white;
}

#btnLimpar:hover {
  background: rgb(194, 6, 6);
  color: white;
}
#img-form {
  width: 130px;
  height: 130px;
  position: relative;
  bottom: 48px;
  left: 35%;
  transform:  rotate(-45deg);
}
#showSucesso1 {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: rgb(99, 196, 99);
}
#showError2 {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: red;
}
</style>