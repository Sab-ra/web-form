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

    <div class="terms">
      <input type="checkbox" v-model="terms_acception" required>
      <label>Accept terms and conditions</label>
    </div>

    <div class="non-required-checkboxes">
      <div>
        <input type="checkbox" value="shaun" v-model="player_names">
        <label>Shaun</label>
      </div>
      <div>
        <input type="checkbox" value="yoshi" v-model="player_names">
        <label>Yoshi</label>
      </div> 
      <div>
        <input type="checkbox" value="mario" v-model="player_names">
        <label>Sabra</label>
      </div> 
    </div>

  </form>

  <p>Email: {{ email_input }}</p>
  <p>Password: {{ password_input }}</p>
  <p>Role: {{ role_selection }}</p>
  <p>Terms accepted: {{ terms_acception }}</p>
  <p>Players: {{ player_names }}</p>


</template>

<script>
export default {
  data() {
    return {
      email_input: '',
      password_input: '',
      role_selection: '',
      terms_acception: false,
      player_names: []
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
  input[ type="checkbox" ] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
  }
</style>