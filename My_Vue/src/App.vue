
<template>
<div class="h-screen w-screen flex flex-col items-center justify-center">
  <form class=" w-80 h-96 bg-gray-100 p-4" action="" @submit.prevent="submit">
    <header class="py-4 text-2xl text-blue-600 text-center font-bold">Form user</header>
    <div class="my-3">
      <label class="text-black text-sm font-semibold block mb-1" for="username">Username</label>
      <input class="text-black text-sm border-1 border-blue-800 font-bold block w-full px-1 py-2 focus:ring focus:ring-blue-500 focus:outline-none" type="text" v-model="username" placeholder="Enter your username" required>
    </div>
    <div class="my-3">
      <label class="text-black text-sm  font-semibold block mb-1" for="password">Password</label>
      <input class="text-black text-sm font-bold block border-1 border-blue-800 w-full px-1 py-2 focus:ring focus:ring-blue-500 focus:outline-none" type="text" v-model="password" placeholder="Enter your password" required>
    </div>
    <button class="w-full bg-green-600 text-gray-100 px-4 py-2 text-sm font-semibold" type="submit">Submit</button>
  </form>
</div>
</template>

<script>
import axios from 'axios';

export default{
  data(){
    return {
      username: "", // model for username
      password: "", // model for password,
      responseText: "" // model for response text
    }
  },
  methods: {
   async submit(){
      try{
      const response =  await axios.post("http://localhost:8080/api/me/my_function", {
          username: this.username,
          password: this.password
        })
        this.responseText = response.data;
        console.log("Response: ", this.responseText);
      }catch(error){
        console.error("There was an error submitting the form!", error);
      }
      // console.log("Username: ", this.username);
      // console.log("Password: " + this.password);
    }
  }
}
</script>

<style scoped>
 
</style>
