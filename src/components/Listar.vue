<template>
    <div class="container">
 <router-link to="/crear" class="btn btn-success"> CREAR EMPLEADO</router-link>
 <br/>
  <br/>
        <div class="card">
        <div class="card-header">
            Empleados
        </div>
        <div class="card-body">
            
            <table class="table">
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>NOMBRE</th>
                        <th>CORREO</th>
                        <th>ACCIONES</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="empleado in empleados" :key="empleado.id">
                        <td>{{empleado.id}}</td>
                        <td>{{empleado.nombre}}</td>
                        <td>{{empleado.correo}}</td>
                        <td>

                       <div class="btn-group" role="group" aria-label="">
                        
                        <router-link :to="{name:'MyEditar', params:{id:empleado.id}}" class="btn btn-primary">EDITAR</router-link>
                        <button type="button" v-on:click="borrarEmpleado(empleado.id)" class="btn btn-danger">BORRAR</button>
                        
                       </div>

                        </td>
                    </tr>
                    <tr>
                        <td scope="row"></td>
                        <td></td>
                        <td></td>
                    </tr>
                </tbody>
            </table>
            
            </div>

         </div>
    </div>
        
    
</template>

<script>
export default {
    data(){
        return{
            empleados:[]
        }
    },
    name:'MyListar',
    created:function(){
    
       this.consultarEmpleados();
    },
    methods:{
         //http://localhost/empleados/


         consultarEmpleados(){
            fetch('https://felipe-developer.000webhostapp.com/api_empleados/')
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta)=>{
                
                console.log(datosRespuesta)
                this.empleados=[]
                if(typeof datosRespuesta[0].success === 'undefined'){
                    this.empleados=datosRespuesta;
                }

            })
            .catch(console.log)
         },
         borrarEmpleado(id){
                console.log(id);
            fetch('https://felipe-developer.000webhostapp.com/api_empleados/?borrar='+id) 
            .then(respuesta=>respuesta.json())
            .then((datosRespuesta)=>{
                
                console.log(datosRespuesta)

               window.location.href="listar"

            })
            .catch(console.log)
         }
    }
}
</script>