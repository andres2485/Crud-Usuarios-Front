<template lang="pug">
   div.uk-container
    .uk-margin
    

    div(class=" card uk-child-width-expand@s uk-text-center" uk-grid)
        div.letras
            div(class="") 
                h3 {{nombreusuario}} {{apellido}} 
        div.letras
            div(class="") 
             nuxt-link(:to="'/posts/' +id")
                button(class="uk-button uk-button-primary") Ver
                    span(uk-icon="icon: forward; ratio: 1")
             button(class="uk-button uk-button-default" style="margin-left:5px", @click="$emit('accionCitacion')") Edit
                    span(uk-icon="icon: file-edit; ratio: 1")
             
         
   
                     
    
    </template>


<script>
export default {
props:['id','nombreusuario','apellido','edad'],
   
methods:{

   
}

    
    
}
</script>


<style scoped>
h3{
    font-weight: bold;
}

.card{

    background: whitesmoke;
   margin-left: 0.5%;
   height: 5rem;
   border-radius: 22px;
}
.letras{

    margin-top:2%;
}
button{
    border-radius: 12px;
}
</style>