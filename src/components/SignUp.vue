<template>
  <form @submit.prevent="submit">
    <label>Email</label>
    <input type="email" required v-model="email">
    <label>Password</label>
    <input type="password" required v-model="password">
    <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
    <label>Role</label>
    <select v-model="role">
        <option value="developer">Web Developer</option>
        <option value="desiginer">Web Desiginer</option>

    </select>
    <div>
        <input type="checkbox" v-model="accept">
        <label>Accept Term and Policy</label>
    </div>
    <div>
        <label>Skills</label>
        <input type="text" @keyup.alt="addSkill" v-model="skill">
    </div>
    <div v-for="skill in skills" :key="skill">
        <p>{{ skill }} <span class="cross" @click="deleteSkill(skill)">&#10006;</span></p>

    </div>
   <div class="aligin">
    <button class="submit">Create Account</button>
   </div>
<!-- multiple checkbox -->
   

  </form>
  <p>email -{{ email }}</p>
  <p>email -{{ password }}</p>
  <p>role -{{ role }}</p>
  <p>accept-{{ accept }}</p>
 
  
  
</template>

<script>
export default {
  data(){
    return {
        email:"",
        password:"",
        role:"",
        accept:false,
        skill:"",
        skills:[],
        errorMessage:""
       
    }
  },
  methods:{
    addSkill(e){
         if(e.key==="," && this.skill)
         {
            this.skills.push(this.skill),
            this.skill=""
         }
    },
    deleteSkill(skill){
       this.skills=this.skills.filter(loopskills=>
       {
        return loopskills!=skill;
       }
      
       )
    },
    submit(){
       if(this.errorMessage.length<8){
        this.errorMessage="Password Should must at least 8 character"
       }
    }
  }
}
</script>

<style>
 form{
     max-width: 420px;
     margin:30px auto ;
     background: white;
     text-align: left;
     padding: 40px;
     border-radius: 10px;
 }
 label{
    color: #aaaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;

 }

 input,select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom:2px solid #ddd;
    color: #555;
 }
 input[type="checkbox"]{
display: inline-block;
width: 16px;
margin: 0 10px 0 0 ;
position: relative;
top: 2px;


 }
 .cross{
    cursor: pointer;
    color: red;
 }
.error{
    color: red;
    font-size: x-small;
}
.submit{
    background: blue;
    padding: 5px;
    border-radius: 20px;
    color: white;
    font-size: x-small;
    margin: 10px auto;
    border-color: aqua;

}

</style>