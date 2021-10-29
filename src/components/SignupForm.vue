<template>
  
<form @submit.prevent="handleSubmit">
    <label>
       Name :
    </label>
    <input type="fullname" required v-model="fullname"><br>
    <label>
       Email :
    </label>
    <input type="email" required v-model="email"><br>
    <label>
    Password :
    </label>
    <input type="password" required v-model="Password"><br>
    <div v-if="passwordError">{{passwordError}} </div>
    <label >Role : </label>

    <select v-model="Role">
        <option value="MERN Developer">Need Developer</option>
        <option value="MEAN Developer">MERN Developer</option>
        <option value="MHVN Developer">MHVN Developer</option>
        <option value="ELECTRON Developer">ELECTRON Developer</option>
        <option value="FLUTTER Developer">FLUTTER Developer</option>
        <option value="REACT NATIVE Developer">REACT NATIVE Developer</option>
        
    </select>

    <br>
    <label>Skills: </label>
    <input type="text" v-model="tempskill" @keyup="addskills">
    <div v-for="skill in skills" :key="skill" >
         <span @click="deleteskill(skill)" >{{skill}}</span>
    </div>

    <div>
        <input type="checkbox" required v-model="terms">
        <label>Accept terms and conditions</label>
    </div>
    <div class="submit">
        <button>create new account  </button>
    </div>

</form>

</template>

<script>
export default {
    data(){
        return {
        fullname:'',
        email:'',
        Password:'',
        Role:'',
        terms:"",
        tempskill:"",
        skills:[ ],
        passwordError:''
        }       
    },
    methods:{
        addskills(e){
            if(e.key=== ',' && this.tempskill)
            {
                if(!this.skills.includes(this.tempskill))
                {
                        this.skills.push(this.tempskill)
                }
                
                this.tempskill=''
            }
        },
        deleteskill(skill){
            this.skills=this.skills.filter((item)=>{
                return skill !== item
            })
        },
        handleSubmit(){
            this.passwordError=this.Password.length > 5 ?
            '': 'password must be 6 char long'
            if(!this.passwordError){
                console.log('Name                 : ',this.fullname);
                console.log('Email                : ',this.email);
                console.log('Password             : ',this.Password);
                console.log('Role                 : ',this.Role );
                console.log('Skills               :',this.skills);
                console.log('terms and conditions :',this.terms);
            }
        }
    }
}
</script>

<style>

</style>