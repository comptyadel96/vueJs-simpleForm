<template>
  <div class="container">
    <form @submit="handleSubmit">
      <label for="email">email:</label>
      <input
        class="input"
        type="email"
        id="email"
        v-model="email"
        placeholder="enter email"
      />
      <label for="password">password:</label>
      <input
        class="input"
        type="password"
        id="password"
        v-model="password"
        placeholder="enter password"
      />
      <label for="role">Role</label>
      <select v-model="role">
        <option value="web">web developer</option>
        <option value="mobile">mobile developer</option>
      </select>

      <div>
        <h1>choose primary skill:</h1>
        <label for="javascript">javascript</label>
        <input type="checkbox" id="javascript" value="js" v-model="languages" />
        <label for="python">python</label>
        <input type="checkbox" id="python" value="python" v-model="languages" />

        <p>another skills you want to mention ?</p>
        <p>please enter the skill and press space to validate it</p>
        <label for="anotherSkils"></label>
        <input
          type="text"
          id="anotherSkils"
          v-model="tempSkill"
          @keypress.space="addSkill"
        />
        <div
          v-for="skill in anotherSkills"
          :key="skill"
          class="pile"
          @click="deleteSkill(skill)"
        >
          {{ skill }}
        </div>
      </div>
      <button class="submit-btn">submit</button>
      <p v-for="error in errors" :key="error" class="error">{{ error }}</p>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Form',
  props: [],

  data() {
    return {
      email: '',
      password: '',
      role: 'web',
      languages: [],
      tempSkill: '',
      anotherSkills: [],
      errors: [],
    }
  },
  methods: {
    addSkill() {
      if (this.tempSkill.trim()) {
        if (!this.anotherSkills.includes(this.tempSkill)) {
          this.anotherSkills.push(this.tempSkill)
        }
        this.tempSkill = ''
      }
    },
    deleteSkill(arrSkill) {
      this.anotherSkills = this.anotherSkills.filter((skill) => {
        return skill !== arrSkill
      })
    },
    handleSubmit(event) {
      event.preventDefault()
      this.errors = []
      if (!this.email || !this.password) {
        return this.errors.push('email and password are required fields')
      }
    },
  },
}
</script>

<style scoped>
form {
  margin: auto;
  padding: 1rem;
  max-width: 60vw;
  position: relative;
  background-color: rgb(241, 241, 241);
  border-radius: 15px;
  text-align: left;
}
label {
  font-size: 1.5rem;
  margin: 0 7px 0 0;
}
.input {
  border: none;
  padding: 0.4rem;
  border-bottom: 1px solid grey;
  display: block;
  width: 70%;
  height: 2rem;
  background-color: transparent;
  margin: 10px 0;
  outline: none;
}
.input:focus {
  border-bottom: 2px solid rgb(37, 255, 17);
  outline: none;
}
select {
  display: block;
}
.submit-btn {
  border: none;
  cursor: pointer;
  padding: 0.7rem;
  background-color: rgb(24, 255, 178);
  color: white;
  font-size: 1.5rem;
  text-align: center;
  margin-left: 50%;
  transform: translate(-50%);
}
.pile {
  padding: 0.5rem 0.7rem;
  border-radius: 1rem;
  background-color: rgb(85, 24, 24);
  color: azure;
  display: inline-block;
  margin: 5px 0.5rem;
  cursor: pointer;
}
.error {
  font-size: 0.7rem;
  color: rgb(245, 39, 80);
  font-weight: bold;
}
</style>
