<template>
  <button class="main-button back">
    <router-link to="/" class="link back"> Powrót </router-link>
  </button>
  <div class="user-enter-container">
    <h1 class="input-heading">Zarejestruj się</h1>
    <form @submit.prevent="register" class="register-form">
      <div class="user-input-box">
        <label for="username" class="input-heading">Nazwa użytownika:</label>
        <input
          type="text"
          id="username"
          class="main-input"
          v-model="username"
          autocomplete="off"
          required
        />
      </div>
      
      <div class="user-input-box">
        <label for="password" class="input-heading">Hasło:</label>
        <input
          type="password"
          id="password"
          class="main-input"
          v-model="password"
          autocomplete="off"
          required
        />
        <button type="submit" class="start-button register">Zatwierdź</button>
        <h2>Co wolisz?</h2>
        <div class="choice-boxes">
      <div class="user-input-box">
        
        <label for="heets" class="input-heading radio-head">Heets</label>
        <input
          type="radio"
          id="heets"
          class="main-input radio"
          v-model="selectedOption"
          value="heets"
          
          required
        />
    
      </div>
      <div class="user-input-box">
        <label  for="cigar"  class="input-heading radio-head">Papieros</label>
        <input
          type="radio"
          id="cigar"
          class="main-input radio"
          v-model="selectedOption"
          value="papieros"
          required
        />
        
      </div>
    </div>
        <span>12345678</span>
      </div>
    
      
    </form>
  </div>
</template>

<script>
import { useAuthStore  } from '../store/modules/store';



export default {
  name: 'RegisterView',
  data() {
    return {
      username: '',
      password: '',
      selectedOption: null,
      colorChanged: false,
    }
  },
  methods: {
    register() {
      const auth = useAuthStore()
      try {
        auth.register({ username: this.username, password: this.password, selectedOption: this.selectedOption  })
        this.$router.push('/LoginView')
      } catch (error) {
        alert(error.message)
      }
    },
    
  }
}

</script>

<style lang="css">
.user-enter-container {
  align-items: center;
}
.main-input {
  padding: 10px;
  margin: 10px;
  width: 200px;
  
}
.user-input-box {
  display: flex;
  flex-direction: column;
  margin-bottom: 10px;
  align-items: center;
}
.input-heading {
  margin-bottom: 5px;
  text-align: center;
}
.choice-boxes {
  display: flex;
  flex-direction: row;
 
}





</style>
