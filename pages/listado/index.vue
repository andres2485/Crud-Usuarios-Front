<template lang="pug">
  
div.uk-container
 
  listado( @accionCitacion="modalCitacion=true" :isOpen="modalCitacion", @closeModal="modalCitacion = false")
  card(v-for="post of res", :key="post.id"  :id="post.id" :nombreusuario="post.nombreusuario" :apellido="post.apellido" :edad="post.edad" @accionCitacion="modalCitacion1=true")
  crearUsuarioModal(:isOpen="modalCitacion", @closeModal="modalCitacion = false")
  editarUsuarioModal(:isOpen="modalCitacion1", @closeModal="modalCitacion1 = false" )
</template>
 


<script>
import listado from '@/components/usuario/listado'
import card from '@/components/usuario/card'
import crearUsuarioModal from '@/components/usuario/crearUsuarioModal'
import editarUsuarioModal from '@/components/usuario/editarUsuarioModal'

export default {

  components:{

  
    listado,
    card,
    crearUsuarioModal,
    editarUsuarioModal
  
  }  ,
  
data(){

  return{
       modalCitacion :false,
        modalCitacion1 :false,
    res:[]
     


  }
},

  
  async asyncData({ query, $axios }) {
    const res = await $axios.$get(
      `http://127.0.0.1:3333/api/v1/usuarios/obtener`
    )
    
    console.log(res)
    return {
      res,
      
    };
  },
}
</script>

<style scoped>
</style>
