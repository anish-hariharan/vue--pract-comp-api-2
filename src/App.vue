<template>
  <section class="container">
    <user-data :first-name="firstName" :second-name="secondName"></user-data>
    <h2>{{pract}}</h2>
    <button @click="add">btn</button>
    <input type="text" placeholder="First Name" @input="setFname">
    <input type="text" placeholder="Second name" ref="snames">
    <button @click="setLast">setLastName</button>
    <input type="text" placeholder="practise" v-model="pract">
  </section>
</template>

<script>
import {ref , computed, watch, provide} from 'vue'
import UserData from './components/UserData.vue';

export default {
  components: {
    UserData
  },
  setup(){
    let firstName = ref('')
    let secondName = ref('')
    let snames = ref(null)
    let pract = ref('')
    let age = ref(20)

    setTimeout(function(){
      userName.value = 'Hariharan',
      age.value = 21
    }, 2000)

    function setFname(event){
      return firstName.value = event.target.value
    }

    function setLast(){
      return secondName.value = snames.value.value
    }

    const userName = computed(function() {
      return firstName.value + ' ' + secondName.value
    })

    function add(){
        return age.value += 20
    }

    watch([userName], function(newValue, oldValue){
      console.log(oldValue[0] + ' ' + newValue[0])
      console.log(oldValue[1] + ' ' + newValue[1])
    })

    provide('userAge', age)

    return{
    userName,
    age,
    add,
    firstName,
    secondName,
    setFname,
    snames,
    pract,
    setLast
  }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>