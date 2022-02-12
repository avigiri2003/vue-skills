<template>
  <div class="hello">
    <div class="holder">
     <form @submit.prevent="addSkill">
        <div>
          <input type="text" placeholder="Enter your skill here and click + button to add the skill" v-model="skillName" v-validate="'min:5'" name="skill"/>
          <button :class="[skillName.length >=5 ? 'addSkillButton' : 'addSkillButtonDisabled']" @click="addSkill" :disabled="skillName.length < 5">+</button>
        </div>
        <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
      </form>
      <ul>
        <li v-for="(mydata, index) in skills" :key='index'> {{ mydata.skill }} 
          <icon-trash class="fa fa-minus-circle" v-on:click="removeSkill(index)"/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data(){
    return {
      skillName: "",
      skills:[
        { "skill": "Vue.js"},
        { "skill": "Java Developer"}
      ]
    }
  },
  methods: {
    addSkill(){
      this.$validator.validateAll().then((result) => {
        if(result){
          if(this.skillName != ""){
            this.skills.push({"skill": this.skillName});
            this.skillName = "";
          }
        }
      })
    },
    removeSkill(id){
      this.skills.splice(id, 1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://stackpath.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

   .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

   input {
    width: calc(100% - 100px);
    border: 0;
    padding: 20px;
    font-size: 20px;
    background-color: #323333;
    color: #687F7F;
  }

  .addSkillButton {
    width: 60px;
    border: 0;
    padding: 20px;
    font-size: 20px;
    background-color:rgb(114, 228, 114);
  }

  .addSkillButtonDisabled {
    width: 60px;
    border: 0;
    padding: 20px;
    font-size: 20px;
    background-color:rgb(206, 199, 199);
  }

  icon-trash {
    float:right;
    cursor:pointer;
  }
</style>
