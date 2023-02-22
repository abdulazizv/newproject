<template>
  <div class="container mx-auto p-20 flex justify-center items-center">
    <form action="#" class="shadow p-5 w-2/3" @submit="adduser">
      <Input labelId="username" inputType="text" placeholder="Enter username" :value="name" @input="$event=> name = $event.target.value"/>
      <Input labelId="email" inputType="email" placeholder="Enter user email" :value="email" @input="$event=> email = $event.target.value" />
      <Button btnType="submit" textContent="Submit" class="border bg-green-500 text-white"/>

    </form>
    
  </div>
</template>
<script>
import Input from '../ui/Input.vue';
import UserView from './UserView.vue';
import Button from '../ui/Button.vue';
import {v4 as uuidv4 } from 'uuid'
import axios from '../service/axios'
import { toast } from 'vue3-toastify'
export default {
  components:{
    Input,
    UserView,
    Button
  },
  data() {
    return {
      name:"",
      email:""
    }
  },
  methods: {
    adduser(e) {
      e.preventDefault();

      const newUser = {
        id:uuidv4(),
        name: this.name,
        email: this.email
      }
      if(newUser.name.length === 0 || newUser.email.length === 0) {
        toast.error(`Please enter a new user name and email`,{
          theme:'dark',
          autoClose:1000,
          position:'top-left'
        })
      } else {
        axios.post('/user',newUser);
        toast.success('User added successfully');
      }
      console.log(newUser)
    }
  },
}
</script>
<style lang="scss">
  
</style>