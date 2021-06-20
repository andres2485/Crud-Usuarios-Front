<template lang="pug">
   div.uk-container
    .uk-margin
     h3(class="uk-card-title") Nombre :  {{post.nombreusuario}} {{post.apellido}}
     p(class="uk-card-title")  Edad : {{post.edad}}
     p(class="uk-card-title")  Ocupación : {{post.ocupacion}}

    button(class="uk-button uk-button-danger" style="margin-left:5px" ,type="button" ,  @click="eliminar()" ) Del
                    span(uk-icon="icon: trash; ratio: 1")
    
      
          
         
</template>

<script>

import axios from 'axios'
export default {
    data(){

        return{

            post:{}
        }
    },
    
async created(){

   

      const res = await axios.get('http://127.0.0.1:3333/api/v1/usuarios/obtenerunusuario/' + this.$route.params.id)
      this.post= res.data
      console.log(res)

  
},
methods:{

     async eliminar(){


           const res = await axios.delete('http://127.0.0.1:3333/api/v1/usuarios/borrar/' + this.$route.params.id)
      this.post= res.data
      console.log(res)
      UIkit.notification({
        message: "🎉 Registro Borrado correctamente",
        status: "primary",
      })
    }
}
}
</script>

<style scoped>

</style>