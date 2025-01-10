<template>
    <div>
      <form action="" @keydown.enter.prevent @submit.prevent="submit">
        <h2>Signup Form</h2>
  
        <!-- Email -->
        <label for="email">Email</label>
        <input type="email" v-model="email" required id="email"><br>
  
        <!-- Password -->
        <label for="password">Password</label>
        <input type="password" v-model="password" id="password"><br>
  
        <!-- Checkbox -->
        <div class="checkbox-container">
          <input type="checkbox" v-model="terms" id="terms">
          <label for="terms">I agree to the terms and conditions</label>
        </div>
  
        <!-- Select -->
        <div class="select-container">
          <label for="profession">Select your profession</label>
          <select id="profession" v-model="profession">
            <option value="webDeveloper">Developer</option>
            <option value="webDesigner">Designer</option>
          </select>
        </div>

        <div class="skills-container">
            <label for="">Skills</label>
            <input class="skill-input" type="text" v-model="skill" @keyup="skillAdd">

            <div class="skills-list">
                <span v-for="skill in skills" :key="skill">{{ skill }}
                    <span @click="deleteSkill(skill)" class="cross" style='font-size:20px;'>&#10008;</span>
                </span>
            </div>
        </div>

        

  
        <!-- Multiple Checkbox -->
        <!-- <div class="skills-container"><br>
          <div>Your Skills</div><br>
          <div class="skills-list" >
            <input type="checkbox" id="html" value="html" v-model="skills">
            <label for="html" >HTML</label>
  
            <input type="checkbox" id="css" value="css" v-model="skills">
            <label for="css" >CSS</label>
  
            <input type="checkbox" id="javascript" value="javascript" v-model="skills">
            <label for="javascript" >Javascript</label>
          </div>
        </div> -->

        <div class="errortext"><p v-if="errMsg">{{ errMsg }}</p></div>
        
        <div class="btn-container">
          <button class="btn" type="create">CREATE ACCOUNT</button>
        </div>

      </form>
    </div>

    {{ email }}<br>
    {{ password }}<br>
    {{ terms }}<br>
    {{ profession }}<br>
    {{ skills }}<br>
    {{ skill }}
  </template>
  
  <script>
  export default {
    data(){
      return{
        email: '',
        password: '',
        terms: false,
        profession: 'webDesigner',
        skills: [],
        skill: '',
        errMsg: ''
      }
    },
    methods: {
        skillAdd(e){
            if(e.keyCode === 13 && this.skill !== ''){  
                this.skills.push(this.skill);
                this.skill = '';
            }
        },
        deleteSkill(skill){
            this.skills = this.skills.filter(loopskill=>{
                return loopskill !== skill
            })
        },
        submit(){
            console.log('submitted');
            if(this.password.length < 6){
                this.errMsg = 'Password must be at least 6 characters';
            }
            if(!this.terms){
                this.errMsg = 'You must agree to the terms and conditions';
            }
        }
    }
}

  </script>
  
  <style>
  /* General Form Styles */
  form {
    width: 400px;
    margin: 20px auto;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 0 8px 0 8px;
    background-color: #f9f9f9;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    font-family: Arial, sans-serif;
  }
  
  h2 {
    text-align: center;
    color: #333;
    font-size: 24px;
    margin-bottom: 20px;
  }
  
  label {
    font-size: 14px;
    color: #333;
    font-weight: bold;
    display: block;
    margin-bottom: 5px;
  }
  
  input[type="email"],
  input[type="password"],
  select {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 0 4px 0 4px;
    font-size: 14px;
    transition: border-color 0.3s ease;
    box-sizing: border-box;
  }
  
  input[type="email"]:focus,
  input[type="password"]:focus,
  select:focus {
    border-color: #007bff;
    outline: none;
  }
  
  /* Checkbox Styles */
  .checkbox-container {
    margin-bottom: 15px;
    display: flex;
    align-items: center;
    font-size: 14px;
    color: #333;
  }
  
  .checkbox-container input[type="checkbox"] {
    margin-right: 10px;
    accent-color: #007bff;
    cursor: pointer;
  }
  
  /* Select Styles */
  .select-container {
    margin-bottom: 15px;
  }
  
  /* Skills Checkbox Styles */
  .skills-container {
    margin-bottom: 15px;
  }
  
  .skills-list {
    display: flex;
    gap: 15px;
    align-items: center;
    margin-top: 20px;
  }
  
  .skills-list input[type="checkbox"] {
    accent-color: #007bff;
  }

  .cross{
    cursor: pointer;
    color: red;
}

.btn-container{
    text-align: center;
}

.btn{
    background-color: #007bff;
    color: white;
    padding: 10px 20px;
    border-radius: 4px 0 4px 0;
    border: none;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.btn:hover{
    background-color: #0056b3;
}

.skill-input{
    padding: 5px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px 0 4px 0;
    font-size: 14px;
    transition: border-color 0.3s ease;
    box-sizing: border-box;
    width: 50%;
}

#profession{
    padding: 5px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 4px 0 4px 0;
    font-size: 14px;
    transition: border-color 0.3s ease;
    box-sizing: border-box;
    width: 50%;
}

.errortext{
    color: red;
    font-size: 12px;
    margin-bottom: 10px;
    font-style: italic;
}


  </style>