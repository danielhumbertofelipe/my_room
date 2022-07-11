<template>
  <div class="container">
      <div class="login">
      <Logo class="logo"/>
      <form action="">
        <div class="input-container">
          <label>Login: </label>
          <input type="text" name="" id="" placeholder="Digite o seu e-mail">
        </div>
        <div class="input-container">
          <label>Senha: </label>
          <input type="password" name="" id="" placeholder="Digite a sua senha">
        </div>
        <div class="input-container">
          <input class="submit-btn" type="submit" value="Login">
        </div>
      </form>
    </div>
  </div>
</template>

<script scoped>
  import Logo from "../components/Logo.vue";
  export default {
    name: "LoginView",
    components: {
      Logo
    }
  }
</script>

<style scoped>
  .container{
    background-color: #ececec;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .login{
    background-color: #d0d0ff;
    width: 600px;
    height: 300px;
    
  }
  .logo{
    font-size: xxx-large;
  }

  label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;;
    padding: 5px 10px;
  }
  input {
    padding: 5px 10px;
    width: 250px;
  }
  .submit-btn {
    background-color: #ececec;
    color: rgb(6, 207, 207);
    font-weight: bold;
    border: 1px solid #222;
    border-radius: 10px;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
    width: 90px;
  }
  .input-container {  
    margin-bottom: 20px;
  }
</style>