<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email_input" />

    <label>Password:</label>
    <input type="password" required v-model="password_input" />
    <div v-if="password_error" class="error">{{ password_error }}</div>

    <label>Role:</label>
    <select required v-model="role_selection">
      <option value="developer">Web developer</option>
      <option value="designer">Web designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="focus_skill" @keyup="addSkill">
    <div v-for="skill in skills" v-bind:key="skill" class="pill">
      <span @click="removeSkill( skill )">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms_acception" required>
      <label>Accept terms and conditions</label>
    </div>

    <div class="submit">
      <button>Create an Account</button>
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
      role_selection: 'developer',
      terms_acception: true,
      focus_skill: '',
      skills: [],
      password_error: ''
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
    removeSkill( skill ) {
      this.skills = this.skills.filter( ( item ) => {
        return skill !== item
      })
    },
    handleSubmit() {
      // validate password
      this.password_error = this.password_input.length > 5 ?
        '' : 'Password must be at least 6 characters long'
      
      // output the information
      if( !this.password_error ) {
        console.log( 'email:', this.email_input )
        console.log( 'password:', this.password_input )
        console.log( 'role:', this.role_selection )
        console.log( 'skills:', this.skills )
        console.log( 'terms accepted:', this.terms_acception )
      }
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
  button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
  }
  .submit {
    text-align: center;
  }
  .error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }
</style>