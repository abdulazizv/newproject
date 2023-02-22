<template lang="">
    <div class="bg-white p-20 w-1/2 auto min-h-[300px] shadow-lg">
        <p class=" text-green-700 text-center text-2xl uppercase font-semibold">Userlist</p>
        <table class="list p-4 bg-green-100 table-auto w-full border-separate">
            <thead class="p-5 bg-green-500 rounded-xl flex justify-between text-black w-full ">
                <th>ID</th> <th>Name</th> <th>Email</th> <th>Edit</th> <th>Remove</th>
            </thead>
            <h1 class="text-center" v-if="userList.length">USERLIST NOT EMPTY</h1>
            <span class="loader" v-if="isLoading"></span>
            <ListItem  v-for="(item, index) in userList" :num="index" :item="item" :key="item.id" :removeUser="removeUser" />
        </table>
    </div>
</template>
<script>
import axios from '../service/axios'
import ListItem from '../ui/ListItem.vue'
export default {
    name:'UserView',
    components:{
        ListItem,
    },
    data() {
        return {
            userList:[],
            isLoading:true
        }
    },
    methods:{
        async getAllUsers()  {
            try {
                const user = await axios.get('/user');
                console.log(user)
                if(user.status == 200) {
                    this.userList = user.data;
                    setTimeout(() => {
                        this.isLoading = false
                    },300)
                }
            } catch (error) {
                console.log(error)
            }
        },
        removeUser(id) {
            axios.delete(`/user/${id}`,{});
        }       
    },
    mounted() {
            this.getAllUsers()
    },
    updated() {
        this.removeUser()
    }
}
</script>
<style scoped>
.loader {
  width: 8px;
  height: 40px;
  border-radius: 4px;
  display: block;
  margin: 20px auto;
  position: relative;
  background: currentColor;
  color: green;
  box-sizing: border-box;
  animation: animloader 0.3s 0.3s linear infinite alternate;
}

.loader::after, .loader::before {
  content: '';
  width: 8px;
  height: 40px;
  border-radius: 4px;
  background: currentColor;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 20px;
  box-sizing: border-box;
  animation: animloader 0.3s  0.45s  linear infinite alternate;
}
.loader::before {
  left: -20px;
  animation-delay: 0s;
}

@keyframes animloader {
  0%   { height: 48px} 
  100% { height: 4px}
}
</style>