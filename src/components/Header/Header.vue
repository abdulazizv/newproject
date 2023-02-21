<template>
     <header class="bg-green-600">
    <div class="container mx-auto">
      <nav class="flex w-full justify-between nav h-[75px] items-center">
        <a href="/" class="text-white uppercase nav-logo text-2xl font-bold">VUE.APP</a>
        <ul class="nav__list flex min-w-[10%] justify-between uppercase">
          <li class="nav__list--item">
            <RouterLink class="nav__list--item-link text-white p-3  mx-2" to="/">Home</RouterLink>
        </li>
          <li class="nav__list--item">
            <RouterLink class="nav__list--item-link text-white p-3  mx-2" to="/userlist">User list</RouterLink>
        </li>
        </ul>
      </nav>
    </div>
  </header>
</template>
<script>
import {RouterLink} from 'vue-router'
export default {
    name:'Header'
}
</script>
<style scoped>
    .router-link-active {
        color:yellow;
        text-decoration: underline;
        font-weight: 900;
    }
</style>