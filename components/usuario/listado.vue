<template lang="pug">
   div.uk-container
    .uk-margin
    div(class="uk-child-width-expand@s uk-text-center" uk-grid)
        div
            div(class="") 
                h3 Usuario
        div
            div(class="") 
                h3 Accion
    .uk-margin
    div(class="", style="margin-left:37%") 
            
                button(class="add uk-button uk-button-primary" style="border-radius:22px" , type="button",  @click="$emit('accionCitacion')") Agregar Nuevo Usuario
                    span(uk-icon="icon: plus; ratio: 1")
    </template>


<script>

export default {
    components:{

       
    }
}
</script>


<style scoped>
h3{
    font-weight: bold;
}
.add{

    background: rgb(122, 180, 63);
}
</style>