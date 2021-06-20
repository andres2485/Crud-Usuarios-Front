<template lang="pug">
    div
        transition(name="bounce", mode="out-in")
            div.uk-position-fixed.uk-position-cover.container-back(v-if="isOpen")
                .container-background
                .modal-container.uk-width-1-4
                    div(class="uk-grid", uk-grid)
                        div(class="uk-width-expand")
                            div
                                h5.uk-margin-remove.uk-text-center Crear Usuario
                        div(class="uk-width-auto")
                            div
                                button(type="button", @click="$emit('closeModal')")  X

                    form.uk-form
                        .uk-child-width-1-2.uk-grid-small.uk-grid(uk-grid)

                      
                                form.uk-form
                                    .uk.uk-grid-small.uk-grid.uk-margin-top(uk-grid)
                                      
                                        div    
                                            label.uk-form-label Nombre
                                            input.uk-input.enter( type="text", v-model="config.nombreusuario")
                                          
                                        
                                     
                                                
                                        div
                                            label.uk-form-label Apellido
                                            input.uk-input.enter( type="text" , v-model="config.apellido")
                                       
                                        div    
                                            label.uk-form-label Edad
                                            input.uk-input.enter(type="number",v-model="config.edad" )
                                        div
                                            label.uk-form-label Ocupación
                                            input.uk-input.enter( type="text" ,v-model="config.ocupacion")
                                          
                                
                        .uk-margin-medium-top.uk-text-right
                            button.uk-button.primary-button( type="button" , @click="guardar") Guardar
</template>

<script>

import axios from 'axios'
export default {
    
      props: ['isOpen'],
    data(){
        return{

            config:{

                nombreusuario:"",
                apellido:"",
                edad:0,
                ocupacion:""
            }
       
        }
    },

    methods:{


        async guardar(){
            let validar=
                this.config.nombreusuario!=0 &&
                this.config.apellido !=0 &&
                this.config.edad !=0 &&
                this.config.ocupacion != 0

                if(validar){
                await  axios.
                post("http://127.0.0.1:3333/api/v1/usuarios/crear",{

                    nombreusuario:this.config.nombreusuario,
                    apellido:this.config.apellido,
                    edad : this.config.edad,
                    ocupacion:this.config.ocupacion
                }).then((response) => {
           
                (this.config.nombreusuario = ""),
              (this.config.apellido = ""),
              (this.config.edad = ""),
              (this.config.ocupacion = ""),
           
              UIkit.notification({
                message: "🎉 Registro Creado correctamente",
                status: "primary",
              });
          })
           .catch((error) => {
            console.log(error);
          });
      }  else {
        UIkit.notification(
          "<span class='uk-margin-small-right'  uk-icon='icon: x'></span> Todos los campos son necesarios.",
          { pos: "top-center", status: "Danger" }
        );
      }
        }
        }
    }
 
    
       

</script>

<style lang="scss" scoped>

    .container-back{
        z-index: 981;
    }

    .container-background{
        height: 100vh;
        width: 100vw;
        top: 0;
        left: 0;
        position: fixed;
        background-color: black;
        z-index: 982;
    }   

    .modal-container{
        background-color: white;
        position: fixed;
        top: 5vh;
        transform: translateX(-50%);
        left: 50%;
        padding: 3rem;
        min-width: 450px;
        border-radius:15 px;
        z-index: 983;
    }

    .uk-input, .uk-select, .uk-textarea{
        border-radius:15px;
    }

.enter{

    width: 350px;
}
</style>