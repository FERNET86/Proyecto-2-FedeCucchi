<template>
    <div class="my-profile">
      <h2>Mi Perfil</h2>
      <div class="profile-field">
        <label>Nombre:</label>
        <span>{{ getUserLogged.nombre }}</span>
      </div>
      <div class="profile-field">
        <label>Apellido:</label>
        <span>{{ getUserLogged.apellido }}</span>
      </div>
      <div class="profile-field">
        <label>Email:</label>
        <span>{{ getUserLogged.email }}</span>
      </div>
      <button @click="closeSession">Cerrar Sesion</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProfileSingle',
    data() {
      return {
        user: {
          username: '',
          email: '',
          location: '',
        }
      };
    },
    computed: {
        getUserLogged() {
            return this.$store.getters.userLogged;
        },
    },
    methods: {
        closeSession() {
        this.$store.commit('setIsLogged', false);
        this.$store.commit('setUserLogged', {});
        this.$router.push('/');
        },
  },
  };
  </script>
  
  <style scoped>
  .my-profile {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5f5f5;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  h2 {
    margin-top: 0;
  }
  
  .profile-field {
    margin-bottom: 10px;
  }
  
  label {
    font-weight: bold;
  }
  
  span {
    margin-left: 5px;
  }
  
  /* Otros estilos según tus necesidades */
  </style>
  