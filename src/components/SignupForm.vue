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

    <label>Skills:</label>
    <input type="text" v-model="focus_skill" @keyup="addSkill">
    <div v-for="skill in skills" v-bind:key="skill" class="pill" @click="removeSkill">
      {{ skill }}
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms_acception" required>
      <label>Accept terms and conditions</label>
    </div>

  </form>

  <p>Email: {{ email_input }}</p>
  <p>Password: {{ password_input }}</p>
  <p>Role: {{ role_selection }}</p>
  <p>Terms accepted: {{ terms_acception }}</p>

</template>

<script>
export default {
  data() {
    return {
      email_input: '',
      password_input: '',
      role_selection: '',
      terms_acception: false,
      focus_skill: '',
      skills: []
    }
  },
  methods: {
    addSkill( e ) {
      if( e.key === ',' || e.key === 'Enter' && this.focus_skill ) {
        if( !this.skills.includes( this.focus_skill )) {
          this.skills.push( this.focus_skill )
        }
        this.focus_skill = ''
      }
    },
    removeSkill( e ) {
      console.log( e )
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
  .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
</style>