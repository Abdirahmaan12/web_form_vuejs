<template>
  <form @submit.prevent="handlesubmit">
    <label>Email:</label>
    <input type="email" required v-model="email">

    <label>Password:</label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">{{ passwordError }}</div>

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

    <label>Skills</label>
    <input type="text" v-model="tempskill" @keyup="addskill">
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteskill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required>
      <label>Accept Terms and Conditions</label>
    </div>

    <div class="submit">
      <button type="submit">Create an Account</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
      role: '',
      terms: false,
      tempskill: '',
      skills: [],
      passwordError: ''
    }
  },
  methods: {
    addskill(e) {
      if (e.key === ',' && this.tempskill) {
        const cleanSkill = this.tempskill.replace(/,/g, '').trim();
        if (cleanSkill && !this.skills.includes(cleanSkill)) {
          this.skills.push(cleanSkill);
        }
        this.tempskill = '';
      }
    },
    deleteskill(skill) {
      this.skills = this.skills.filter(item => item !== skill);
    },
    handlesubmit() {
      this.passwordError = this.password.length >= 5 ? '' : 'Password must be at least 5 characters';
      if (!this.passwordError) {
        this.email = '';
        this.password = '';
        this.role = '';
        this.terms = false;
        this.tempskill = '';
        this.skills = [];
        this.$emit('form-success');
      }
    }
  }
}
</script>

<style>

form {
  max-width: 400px;
  margin: 30px auto;
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

input[type="checkbox"] {
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
