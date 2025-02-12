<template>
    <div>
      <form @submit.prevent="checkPassword">
        <label for="password">Mot de passe</label>
        <input v-model="password" type="password" id="password" required />
        <span v-if="!isPasswordValid" class="error">Le mot de passe doit contenir au moins 8 caractères, une majuscule, une minuscule, et un chiffre.</span>
        <button type="submit" :disabled="!isPasswordValid">Soumettre</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        password: "",
      };
    },
    computed: {
      isPasswordValid() {
        const regex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/;
        return regex.test(this.password);
      },
    },
    methods: {
      checkPassword() {
        alert("Mot de passe validé !");
      },
    },
  };
  </script>
  
  <style scoped>
  .error {
    color: red;
  }
  </style>
  