<template lang="pug">
  
   div.uk-container
    nav(class="uk-navbar-container uk-margin" uk-navbar)
        div(class="uk-navbar-left")

             a(class="uk-navbar-item uk-logo" href="#") Crud

             ul(class="uk-navbar-nav")
                li
                    nuxt-link(to="/home")
                        span(class="uk-icon uk-margin-small-right" uk-icon="icon: home")
                        p Inicio
                    

                li
                    nuxt-link(to="/listado/")
                        span(class="uk-icon uk-margin-small-right" uk-icon="icon: user")
                        p Usuarios
                li
                    nuxt-link(to="/about/")
                        span(class="uk-icon uk-margin-small-right" uk-icon="icon: location")
                        p About
        

            
</template>>
 
<script>
export default {
  
}
</script>

<style scoped>

.uk-navbar-container,p,a,span,button{

  background: black;
  color: white;
  font-weight: bold;
}

button{

  margin-left:5px;
}
</style>
