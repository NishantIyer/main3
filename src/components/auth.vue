<template>
  <div class="container">
    <div v-if="loggedIn" class="content">
      Hey, Kindly visit <a :href="link" target="_blank">this</a>
    </div>
    <div v-else class="login-container glass-effect">
      <div class="hint">Hint: L.bri..ti.n</div>
      <input type="password" v-model="password" placeholder="Enter Password" class="password-input" />
      <button @click="login">Log In</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      password: "",
      loggedIn: false,
      link: "https://ny.netlify.app",
    };
  },
  methods: {
    login() {
      if (this.password === "Lubrication") {
        this.loggedIn = true;
      } else {
        alert("Incorrect password");
      }
    },
  },
};
</script>

<style scoped>
.container {
  background-color: #212121;  /* Material Black */
  color: white;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.glass-effect {
  backdrop-filter: blur(20px) saturate(200%);
  background-color: rgba(33, 33, 33, 0.7);  /* Transparent Material Black */
  border-radius: 15px;
  padding: 20px;
  width: 300px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.login-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.hint {
  margin-bottom: 10px;
  font-size: 1.2em;
}

.password-input {
  background-color: #212121;  /* Material Black */
  color: white;
  padding: 10px;
  margin-bottom: 10px;
  border: none;
  border-radius: 5px;
  font-size: 1em;
}

button {
  padding: 10px;
  background-color: #555;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.content {
  font-size: 1.2em;
}
</style>
