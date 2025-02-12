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
</template>

<script>
export default {};
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