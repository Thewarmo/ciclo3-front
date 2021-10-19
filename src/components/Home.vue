<template>

    <div class="container">
        <div class="titulo">
            <h1>¡Bienvenido  <span> {{username}} </span>!</h1>
            <hr>
        </div>
        
        
        <br>
        <!-- carrusel -->
        <div class="card text-center">
  <div class="card-header">
    <ul class="nav nav-tabs card-header-tabs">
      <li class="nav-item">
        <a class="nav-link" aria-current="true" href="#" @click="activo='Informacion',informacion">Informacion</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#" @click="activo='Modificar',modificar">Modificar</a>
      </li>
      <li class="nav-item">
        <a class="nav-link">Contacto</a>
      </li>
    </ul>
  </div>
  <div class="card-body">
    <h5 class="card-title" v-if="activo ==='Informacion'"><strong>Informacion de {{username}} </strong></h5>
    <h5 class="card-title" v-else> No hay informacion disponible</h5>
    <p class="card-text" v-if="activo ==='Informacion'">aqui podras encontrar toda la informacion del usuario {{username}},por el momento solo tiene el username.</p>
    <a href="#" class="btn btn-primary" v-if="activo ==='Informacion'" @click="logOut">Cerrar sesion</a>
  </div>
</div>
        <!-- fin carrusel -->
    </div>

</template>


<script>

export default {
    name: "Home",

    data: function(){
        return {
            username: localStorage.getItem('username') || "none",
            activo : ""
        }
    },
    methods:{
        verifyAuth: function() {
      this.is_auth = localStorage.getItem("isAuth") || false;
		
			if (this.is_auth == false)
        this.$router.push({ name: "logIn" });
      else
        this.$router.push({ name: "home" });
    },
        informacion(){
            console.log(this.activo);
        },
        modificar(){
            console.log(this.activo)
        },
        logOut(){
            localStorage.clear();
			alert("Sesión Cerrada");
			this.verifyAuth();

        }
    }
}

</script>


<style>
    .titulo{
        margin: 0;
        padding: 0%;
        height: 100%;
        width: 100%;
    
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .titulo h1{
        font-size: 50px;
        color: #283747;
    }

    .titulo span{
        color: crimson;
        font-weight: bold;
    }
</style>