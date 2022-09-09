<template>
  
<nav class="navbar navbar-expand navbar-light bg-light">
   <div class="navbar navbar-nav">

   <router-link to="/" class="nav-link"> HOME</router-link>           
   <router-link to="/crear" class="nav-link"> CREAR</router-link>
   <router-link to="/listar" class="nav-link">EMPLEADOS</router-link>
               
    </div>  
    
</nav>



  
  <router-view/>
</template>


