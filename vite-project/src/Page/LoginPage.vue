<template>
  <div>
    <div>
      <h2>Connexion</h2>
      <form @submit.prevent="handleSubmit">
        <div>
          <label>Email</label>
          <input v-model="email" type="email" placeholder="Entrez votre email" />
          <p v-if="emailError" class="text-red">{{ emailError }}</p>

          <label>Mot de passe</label>
          <input v-model="password" type="password" placeholder="Entrez votre mot de passe" />
          <p v-if="passwordError" class="text-red">{{ passwordError }}</p>
        </div>
        <button type="submit">Se connecter</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      emailError: "",
      passwordError: "",
    };
  },
  methods: {
    validateEmail(email) {
      const regex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
      return regex.test(email);
    },
    validatePassword(password) {
      const regex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/;
      return regex.test(password);
    },
    handleSubmit() {
      this.emailError = this.validateEmail(this.email) ? "" : "Adresse e-mail invalide";
      this.passwordError = this.validatePassword(this.password) 
        ? "" 
        : "Le mot de passe doit contenir au moins 8 caractères, une lettre minuscule, une lettre majuscule et un chiffre.";

      if (!this.emailError && !this.passwordError) {
        alert("Connexion réussie !");
      }
    },
    
  },
};
</script>
