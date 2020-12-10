<template>
  <form @submit.prevent="submit">
      <label for="">Email</label>
      <input type="email" required v-model="email">

      <label for="">Password</label>
      <input type="password" v-model="password">
      <p v-if="errorMsg" class="error">{{errorMsg}}</p>
      <label for="">Roles:</label>
      <select v-model="role">
        <option value="develper">Web Developer</option>
        <option value="designer">Web Designer</option>
      </select>

      <div>
        <label for="">Skills</label>
        <input type="text" @keyup.alt="addSkill" v-model="skill">
      </div>
      <div v-for="skill in skills" :key="skill">
        <p>{{skill}} <span class="cross" @click="deleteSkill(skill)">&#x2716;</span></p>
      </div>
    <!-- single checkbox -->
      <div>
          <input type="checkbox" v-model="accept">
          <label for="">Accept Terms and condition</label>
      </div>
      <div class="align">
        <button class="create">Create Account</button>
      </div>
  </form>
  <p>email- {{email}}</p>
  <p>password-{{password}}</p>
  <p>role-{{role}}</p>
  <p>accept -{{accept}}</p>

</template>

<script>
export default {
    data(){
      return {
        email:"hmt@gmail.com",//ab
        password:"",//
        role:"designer",
        accept:true,
        skills:[],
        skill:"",
        errorMsg:""
     }
    },
    methods:{
      addSkill(e){
        if(e.key==="," && this.skill){
            this.skills.push(this.skill);
            this.skill=""
        }
      },
      deleteSkill(skill){ //php
        this.skills=this.skills.filter(loopSkill=>{ //html,php,css
         
          return loopSkill!=skill; 
        })
      },
      submit(){
        // validation
        if(this.password.length<8){
          this.errorMsg="Password Must me at least 8 characters" 
        }
      }
    }
}
</script>

<style>
    form {
        max-width: 420px;
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
      input,select {
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
      .cross{
        cursor: pointer;
        color:red
      }
      
      .create{
        background-color: royalblue;
        padding:8px;
        color: white;
        border-radius: 10px;
      }
      .align{
        text-align: center;
      }
      .error{
        color:crimson;
      }
</style>