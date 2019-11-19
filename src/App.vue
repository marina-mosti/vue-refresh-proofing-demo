<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <hr />
    <form>
      <label for="firstName">First Name</label>
      <input type="text" id="firstName" @input="updateForm('firstName', $event.target.value)" :value="form.firstName" />

      <label for="lastName">Last Name</label>
      <input type="text" id="lastName" @input="updateForm('lastName', $event.target.value)" :value="form.lastName" />

      <label for="email">Email</label>
      <input type="email" id="email" @input="updateForm('email', $event.target.value)" :value="form.email" />

      <label for="framework">Favorite Framework</label>
      <select id="framework" @change="updateForm('framework', $event.target.value)">
        <option value="vue" :selected="form.framework === 'vue'">Vue</option>
        <option value="stillvue" :selected="form.framework === 'stillvue'">Vue!</option>
        <option value="vuevuevue" :selected="form.framework === 'vuevuevue'">Vue :D</option>
        <option value="okfine" :selected="form.framework === 'okfine'">Other</option>
      </select>

      <label for="extras">Heres an extra space to describe why you love Vue</label>
      <textarea id="extras" @input="updateForm('extras', $event.target.value)" :value="form.extras" rows="5"></textarea>

      <label>
        <input type="checkbox" :checked="form.spam" @change="updateForm('spam', $event.target.checked)" />
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
      form: {
        firstName: '',
        lastName: '',
        email: '',
        framework: 'vue',
        extras: '',
        spam: true
      }
    }
  },
  methods: {
    openStorage () {
      return JSON.parse(localStorage.getItem('form'))
    },
    saveStorage (form) {
      localStorage.setItem('form', JSON.stringify(form))
    },
    updateForm (input, value) {
      this.form[input] = value

      let storedForm = this.openStorage()
      if (!storedForm) storedForm = {}

      storedForm[input] = value
      this.saveStorage(storedForm)
    }
  },
  created () {
    const storedForm = this.openStorage()
    if (storedForm) {
      this.form = {
        ...this.form,
        ...storedForm
      }
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
