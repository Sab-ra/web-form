<template>
  <form>
    <label>Email:</label>
    <input type="email" required v-model="email_input" />

    <label>Password:</label>
    <input type="password" required v-model="password_input" />

    <label>Role:</label>
    <select required v-model="role_selection">
      <option value="developer">Web developer</option>
      <option value="designer">Web designer</option>
    </select>

  </form>
  <p>Email: {{ email_input }}</p>
  <p>Password: {{ password_input }}</p>
  <p>Role: {{ role_selection }}</p>
</template>

<script>
export default {
  data() {
    return {
      email_input: '',
      password_input: '',
      role_selection: ''
    }
  }

}
</script>

<style>
  form {
    max-width: 240px;
    margin: 16px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
  }
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
  }
</style>