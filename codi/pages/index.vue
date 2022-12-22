<template>
  <v-container>

    <v-row>
      <v-col cols="12" v-for="todoVue in todosVue">
          <div>{{todoVue.todoVue}}</div>
          <div v-if="completed">feta</div>
          <div v-else>per fer</div>
          <div>{{todoVue.userId}}</div>
      </v-col>
    </v-row>
   
  </v-container>
</template>

<script>
  import axios from "axios"
       
  export default{
      mounted(){
        this.descarregarTodos()
      },
      methods:{
        descarregarTodos(){
              axios.get('https://dummyjson.com/todos')
                  .then(resposta => {
                    console.log(resposta)
                    this.todosVue = resposta.data.todos
                    this.respostaVue = resposta
                  })
                  .catch(function(err){
                    console.log(err)
                  })
              }
          },
      data(){
        return {
          todosVue :null,
          respostaVue: null
      }
    }
  }
</script>