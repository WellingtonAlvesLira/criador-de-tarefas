<template >
<div>
  <v-col id="footeer">
    {{ new Date().getFullYear() }} — <strong>Criador de Tarefas</strong>
  </v-col>
</div>
</template>

<script>
export default {
  name: 'FooterTarefa'

}
</script>

<style scoped>
#footeer {
  margin-top: 70px;
  text-align: center;
  color: black;
}
</style>