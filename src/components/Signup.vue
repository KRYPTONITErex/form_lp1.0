<template>
    <p>Signup Form</p>
    <form action="">
      <div>
        <label>Email</label>
        <input type="email" required v-model="email">
        <hr>
        
        <label>Password</label>
        <input type="password" required v-model="password">
        <hr>
        
        <div class="role-selection">
          <label for="role">Roles:</label>
          <select id="role" v-model="role">
            <option value="webDeveloper">Developer</option>
            <option value="webDesigner">Designer</option>
          </select>
        </div><hr>

        <div>
            <input type="checkbox" v-model="accept">
            <label>I agree to the terms and conditions</label>  
        </div><br>

        <div>
            <label for="">Skills  : </label>
            <input type="text" @keyup="addSkill" v-model="skill">
        </div>

        <div class="skill-container">
            <div v-for="skill in skills" :key="skill" class="skill-item">
                <p>{{ skill }}</p><span @click="deleteSkill(skill)" class="cross" style='font-size:20px;'>&#10008;</span>
            </div>
        </div>

<!--      
        <label>Check Names</label>
        <div>
            <input type="checkbox" value="Lwin Phyo" v-model="names">
            <label for="Lwin">Lwin</label>
        </div>
        <div>
            <input type="checkbox" value="Phyo Lwin" v-model="names">
            <label for="Phyo">Phyo</label>
        </div>
        <div>
            <input type="checkbox" value="Khaing Zar" v-model="names">
            <label for="Khaing">Khaing</label>
        </div> -->
        

      </div>
    </form>
  
    <p>email - {{ email }}</p>
    <p>password - {{ password }}</p>
    <p>role - {{ role }}</p>
    <p>accept - {{ accept }}</p>
    <!-- <p>names - {{ names }}</p> -->
    <p>skill - {{ skill }}</p>
    <p>skills data - {{ skills }}</p>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: '',
        password: '',
        role: 'webDeveloper',
        accept: false,
        // names: []
        skills: [],
        skill: ''
      };
    },
    methods: {
      addSkill(e) {
        // console.log(e.key)
        if(e.keyCode === 13 ){
            this.skills.push(this.skill)
            this.skill=''
        }
      },
      deleteSkill(skill){
        // console.log( "delete - " + skill) 
        this.skills = this.skills.filter(loopskill=>{
            return loopskill !== skill})
      }
    }
  };
  </script>
  
  <style>
  form {
    text-align: left;
    background-color: #f9f9f9;
    display: flex;
    flex-direction: column;
    width: 400px;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    margin: 20px auto;
    font-family: Arial, sans-serif;
  }
  
  form > p {
    text-align: center;
    font-size: 20px;
    font-weight: bold;
    color: #333;
    margin-bottom: 20px;
  }
  
  form > div {
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
  }
  
  form > div label {
    font-size: 14px;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  form > div input {
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    transition: border-color 0.3s ease;
  }
  
  form > div input:focus {
    border-color: #007bff;
    outline: none;
  }
  
  .role-selection {
    display: flex;
    align-items: center;
    margin-top: 15px;
  }
  
  .role-selection label {
    font-size: 14px;
    font-weight: bold;
    margin-right: 10px;
  }
  
  .role-selection select {
    padding: 10px;
    font-size: 14px;
    border: 1px solid #ccc;
    border-radius: 4px;
    background-color: #fff;
    color: #333;
    transition: border-color 0.3s ease;
    appearance: none; /* Removes the default OS styling for a consistent look */
  }
  
  .role-selection select:focus {
    border-color: #007bff;
    outline: none;
  }
  
  .role-selection select option {
    padding: 10px;
  }
  
  form > button {
    background-color: #007bff;
    color: #fff;
    border: none;
    padding: 12px;
    font-size: 16px;
    font-weight: bold;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  form > button:hover {
    background-color: #0056b3;
  }
  
  form > small {
    text-align: center;
    display: block;
    margin-top: 10px;
    color: #666;
    font-size: 12px;
  }
  input[type="checkbox"] {
  width: 16px;
  height: 16px;
  cursor: pointer;
  accent-color: #007bff; /* Adds a custom color for supported browsers */
  }

  .skills-container {
    margin: 5px;
  display: flex;
  flex-wrap: wrap;
  gap: 10px; /* Space between each skill item */
}

.skill-item {
    margin: 5px;
  display: inline-block;
  align-items: center;
  gap: 5px; /* Space between text and cross icon */
  background-color: #f0f0f0;
  padding: 5px 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.skill-item p {
  margin: 5px;
  font-size: 14px;
}

.cross {
  color: red;
  cursor: pointer;
  font-size: 16px;
}
</style>