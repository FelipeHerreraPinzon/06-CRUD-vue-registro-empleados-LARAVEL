<template>
    <div class="container">

            <div class="card">
            <div class="card-header">
                Agregar Nuevo Empleado
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="agregarRegistro">

    <div class="mb-3">
      <label for="nombre" class="form-label">NOMBRE:</label>
      <input type="text" class="form-control" name="nombre" v-model="empleado.nombre" id="nombre" aria-describedby="helpId" placeholder="Ingresa Nombre" required>
      
    </div>

    <div class="mb-3">
      <label for="correo" class="form-label">CORREO:</label>
      <input type="email" class="form-control" name="correo" v-model="empleado.correo" id="correo" aria-describedby="helpId" placeholder="Ingresa Correo" required>
      
    </div>

    <div class="btn-group" role="group" aria-label="">
        <button type="submit" class="btn btn-success">AGREGAR</button>
        
        <router-link :to="{name:'MyListar'}" class="btn btn-danger">CANCELAR</router-link>

        
        
    </div>

    </form>



            </div>
            
        </div>
        
    </div>
</template>

<script>
export default {
    name:'MyCrear',
    data(){
         return{
            empleado:{}
         }
    },
    methods:{
        agregarRegistro(){
            console.log(this.empleado);
            var datosEnviar = {nombre:this.empleado.nombre, correo:this.empleado.correo}
            fetch('https://felipe-developer.000webhostapp.com/api_empleados/?insertar=1', {
                method:"POST",
                body:JSON.stringify(datosEnviar)

            })
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta=>{
                console.log(datosRespuesta);
                window.location.href='listar'
            }))
        }
    }
}
</script>