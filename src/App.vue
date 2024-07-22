<script>
  export default{
    name: 'App',
    data(){
      return{
        greet: 'Welcome',
        name: 'Ferdinand',
        count: 0,
        hobbies: ['Playing', 'Sleeping', 'Eating'],
        age: 24,

        formValues: {
          name: '',
          address: '',
          email: '',
          age: '',
          country: '',
          gender: '',
        },
      } 
    },

    methods:{
      decrease(){
      this.count--;
    },

    reset(){
      this.count = 0;
    },

    increase(){
      this.count++;
    },

    changeName(){
      this.name = "CabualisM"
    },

    showInfo(hobbies){
      console.log(hobbies);
    },
    
    submitForm(event){
        event.preventDefault()
        console.log(`Form Data:`, this.formValues)
      }
    }
  }
</script>


<template>

  <h1>{{ greet }} {{ name }}</h1>
  <button @click="changeName()">Change Name</button><br><br>
  <button @click="showInfo(hobbies)">Show Information</button>
  <div>
    <h2>Counter</h2>
    <h2 class="color">{{ count }}</h2>
    <button @click="decrease()">-</button>
    <button @click="reset()">Reset</button>
    <button @click="increase()">+</button>
  </div>

  <div class="age">
    <h2>Age</h2>
    <h2 class="color" v-if="age >= 18">You have Permission to Enter this Website!</h2>
    <h2 class="color" v-else-if="age <18">You dont have Permission to Enter this Website!</h2>
    <h2 class="color" v-else>Enter Valid Age</h2>
  </div>


  <div>
    <pre>
      {{ JSON.stringify(formValues, null, 2 ) }}
    </pre>
   </div>

   <!-- v-model.trim="" / remove white spaces -->
   <!-- v-model.number="" / turn string to number -->

  <form @submit="submitForm">
    <label for="name">Enter Name:</label><br>
    <input type="text" id="name" v-model.trim="formValues.name"><br><br>

    <label for="address">Enter Adress</label><br>
    <input type="text" id="address" v-model="formValues.address"><br><br>

    <label for="email">Enter Email</label><br>
    <input type="email" id="email" v-model="formValues.email"><br><br>

    <label for="age">Enter Age:</label><br>
    <input type="number" id="age" v-model.number="formValues.age"><br><br>

    <div class="country">
      <label>Select Country</label><br>
        <select id="country" v-model="formValues.country">
          <option value="">Select a Country</option>
          <option value="Philippines">Philippines</option>
          <option value="Vietnam">Vietnam</option>
          <option value="Indonesia">Indonesia</option>
          <option value="Cambodia">Cambodia</option>
        </select>
    </div><br>

    <div class="gender">
      <label>Select Gender</label><br><br>

        <input type="radio" id="male" value="Male" name="gender" v-model="formValues.gender">
        <label for="male">Male</label><br>

        <input type="radio" id="female" value="Female" name="gender" v-model="formValues.gender">
        <label for="female">Female</label>
    </div>

    <!-- Keyboard Event Modifier (@keyup.enter="") / Press enter to submit the Form -->
    <button @keyup.enter="submitForm">Submit</button>
  </form>

  <!-- Bonus Directives -->
  

</template>

<style>
  .color{
    color: red;
  }
</style>