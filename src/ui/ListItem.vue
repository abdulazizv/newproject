<template>
  <tr
    class="px-5 bg-green-500 rounded-xl items-center my-2 py-3"
  >
    <td><strong>{{num + 1}}</strong></td>
    <td><span>{{item.name}}</span></td>
    <td><span>{{item.email}}</span></td>
    <td>
    <button
      class="bg-cyan-600 focus:ring-2 focus:ring-cyan-200 px-4 py-2 duration-200 rounded-2xl text-white"
    >
      Edit
    </button>
</td>
<td>
    <button
      @click="removeUser(item.id)" class="bg-red-600 focus:ring-2 focus:ring-cyan-200 px-4 py-2 duration-200 rounded-2xl text-white"
    >
      Remove
    </button>
</td>
  </tr>
</template>
<script>
export default {
  name: "ListItem",
  props: {
    num: [String,Number],
    item:Object,
    removeUser:Function
  },
};
</script>
<style lang="scss"></style>
