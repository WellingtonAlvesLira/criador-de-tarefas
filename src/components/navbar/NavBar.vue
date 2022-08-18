<template>
  <v-container container>
    <div id="nav_bar">
      <img
        id="img_nav_bar"
        src="https://img.freepik.com/fotos-gratis/bloco-de-anotacoes-com-lista-de-tarefas-na-vista-superior-da-mesa_23-2148938741.jpg?w=740&t=st=1660588730~exp=1660589330~hmac=d4bc1deb1ed03c06da8cf5bdba81a96aed33ce209fe9bf50de4ca02f1b8fce6f"
        alt=""
      />

      <h2 id="title1">Criador</h2>
      <h2>de</h2>
      <h2 id="title2">Tarefas</h2>
      <ul id="menu_tarefa">
        <li><router-link to="/">Home</router-link></li>
        <li><router-link to="/about">Tarefas</router-link></li>
      </ul>
    </div>
  </v-container>
</template>


<script>
export default {
  name: "NavBar",
};
</script>

<style scoped>
#nav_bar {
  padding: 10px;
  margin-bottom: 20px;
  background: rgba(255, 255, 255, 0.87);
}

#menu_tarefa {
  list-style: none;
  text-align: right;
}

#menu_tarefa li{
display: inline;
margin: 5px;

}

#menu_tarefa li:hover{
  background: rgba(255, 255, 255, 0.87);
}

#menu_tarefa a{
  text-decoration: none;
  color: rgb(24, 24, 66);
  font-weight: 500;

}

#menu_tarefa a:hover{
  color: rgb(24, 24, 66);
  background: rgba(36, 101, 138, 0.527);
  padding: 10px;
}

#img_nav_bar {
  width: 200px;
  margin-right: 10px;
  border-radius: 60px;
  position: relative;
  animation: mymove 5s infinite;
  animation-delay: 2s;
}

h2 {
  display: inline;
  margin-right: 10px;
}

#title1 {
  color: rgb(24, 24, 66);
}
#title2 {
  color: rgb(187, 65, 86);
}

@keyframes mymove {
  from {
    left: 0px;
  }
  to {
    left: 400px;
  }
}
</style>