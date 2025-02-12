<template>
  <header class="header">
    <h1>Mon Application</h1>
    <nav>
      <ul>
        <li><router-link to="/">Accueil</router-link></li>
        <li><router-link to="/login">Connexion</router-link></li>
      </ul>
    </nav>
  </header>
  <div>
    <div>
      <h2>Connexion</h2>
      <form @submit.prevent="handleSubmit">
        <div>
          <label>Email <span v-if="!email" class="text-red">❌</span></label>
          <input v-model="email" type="email" placeholder="Entrez votre email" @input="validateEmail" />
          <p v-if="emailError" class="text-red">{{ emailError }}</p>
        </div>
        <div>
          <label>Mot de passe <span v-if="!password" class="text-red">❌</span></label>
          <input v-model="password" type="password" placeholder="Entrez votre mot de passe" @input="validatePassword" />
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
  watch: {
    email(value) {
      if (!value) {
        this.emailError = "L'email est requis";
      } else {
        this.validateEmail();
      }
    },
    password(value) {
      if (!value) {
        this.passwordError = "Le mot de passe est requis";
      } else {
        this.validatePassword();
      }
    },
  },
  methods: {
    validateEmail() {
      const regex = /^[a-zA-Z0-9._%+-]{3,30}[@][a-zA-Z0-9.-]{3,20}\.[a-zA-Z]{2,5}$/;
      this.emailError = regex.test(this.email) ? "" : "Email invalide";
    },
    validatePassword() {
      const regex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/;
      this.passwordError = regex.test(this.password)
        ? ""
        : "Le mot de passe doit contenir au moins 8 caractères, une lettre minuscule, une lettre majuscule et un chiffre.";
    },
    handleSubmit() {
      this.validateEmail();
      this.validatePassword();
      
      if (!this.emailError && !this.passwordError) {
        this.$router.push("/");
      }
    },
    resetForm() {
      this.email = "";
      this.password = "";
      this.emailError = "";
      this.passwordError = "";
    }
  },
  mounted() {
    this.resetForm();
  }
};
</script>

<style scoped>
.header {
  background: #333;
  color: white;
  padding: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
nav ul {
  display: flex;
  list-style: none;
  gap: 15px;
}
nav ul li a {
  color: white;
  text-decoration: none;
}
.text-red {
  color: red;
  margin-left: 10px;
}
</style>
