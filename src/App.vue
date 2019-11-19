<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <hr />
    <form>
      <label for="firstName">First Name</label>
      <input type="text" id="firstName" v-model="firstName" />

      <label for="lastName">Last Name</label>
      <input type="text" id="lastName" v-model="lastName" />

      <label for="email">Email</label>
      <input type="email" id="email" v-model="email" />

      <label for="framework">Favorite Framework</label>
      <select id="framework" v-model="framework">
        <option value="vue">Vue</option>
        <option value="stillvue">Vue!</option>
        <option value="vuevuevue">Vue :D</option>
        <option value="okfine">Other</option>
      </select>

      <label for="extras">Heres an extra space to describe why you love Vue</label>
      <textarea id="extras" v-model="extras" rows="5"></textarea>

      <label>
        <input type="checkbox" v-model="spam" />
        I want all the spams
      </label>

      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      firstName: '',
      lastName: '',
      email: '',
      framework: 'vue',
      extras: '',
      spam: false
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

form {
  width: 300px;
  margin: 0 auto;
  text-align: left
}

label, input, select, textarea {
  display: block;
  width: 100%;

  input {
    display: inline;
    width: auto;
  }
}
</style>
