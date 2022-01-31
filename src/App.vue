<template>
  <div class="container">
    <h2>{{ titulo }}</h2>
    <div class="input-group">
     <input @keyup.enter="adicionarTarefa" v-model="novaTarefa" type="text"> 
     <span class="input-group-btn">
        <button @click="adicionarTarefa" class="btn btn-primary">Adicionar</button>
       </span>
    </div>
    <footer>
      <em> Altere aqui o título da sua lista de tarefas</em>
      <input v-model="titulo" type="text"> 
      <listartarefa :tarefas="tarefas"/>
    </footer>
  </div>
</template>

<script>

import listartarefa from "@/components/listartarefa/"

export default {
  name: 'App',
  components: {
    listartarefa
    
  },
  data () {
    return {
        titulo: "Minha Lista de Tarefas ",
        novaTarefa: '',
        tarefas: [
          { titulo: "Estudar", checked: false},
          { titulo: "Programar", checked: true},
        ]
    };
  },
    methods: {
      adicionarTarefa() {
        this.tarefas.push({
          titulo: this.novaTarefa,
          checked: false
        })
        this.novaTarefa="";
      }
    }
  
};
</script>

<style>
.container {
  width: 40%;
  margin: 20px auto 0px auto;
}

  ul li {
    list-style: none;
  }

  .removed {
    color:pink;
  }

  .removed label {
    text-decoration: line-through;
  }
</style>
