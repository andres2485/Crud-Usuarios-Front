<template lang="pug">
  
div.uk-container
  navegacion
  home
  listado

</template>
 


<script>
import navegacion from '@/components/navegacion'
import home from '@/components/home'
import listado from '@/components/usuario/listado'

export default {

  components:{

    navegacion,
    home,
    listado
  }
}
</script>

<style scoped>
</style>
