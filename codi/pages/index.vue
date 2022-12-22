<template>
  <v-container>

    <v-row>
      <v-col cols="12" v-for="todoVue in todosVue">
          <div>{{todoVue.todoVue}}</div>
          <div v-if="todoVue.completed">feta</div>
          <div v-else>per fer</div>
          <div>{{donamElNom(todoVue.userId)}}</div>
        
      </v-col>
      <v-col cols="12" sm="6">
        <div>{{usersVue}}</div>
      </v-col>
    </v-row>
   
  </v-container>
</template>

<script>
  import axios from "axios"
       
  export default{
      mounted(){
        this.descarregarTodos(),
        this.descarregarUsuaris()
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
              },
        descarregarUsuaris(){
          axios.get('https://dummyjson.com/users')
                  .then(respostaUsers => {
                    console.log("la lista de users", respostaUsers)
                    this.usersVue = respostaUsers.data.users
                    this.respostaVue = respostaUsers
                  })
                  .catch(function(err){
                    console.log(err)
                  })
              },
        donamElNom(userId){
              if(this.usuaris){
                this.usuaris.forEach(usuari=>
                )
              }
            }
          },
      data(){
        return {
          todosVue :null,
          respostaVue: null,
          usersVue: null,
          respostaUsers:null
      }
    }
  }
</script>