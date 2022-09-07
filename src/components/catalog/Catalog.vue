<script setup lang="ts">
import {reactive} from "vue";

const state: { posts: IPost[] } = reactive({
  posts: [
    {
      id: 1,
      userID: 1,
      title: 'sunt aut facere repellat provident occaecati excepturi optio reprehenderit',
      body: 'quia et suscipit\\nsuscipit recusandae consequuntur expedita et cum\\nreprehenderit molestiae ut ut quas totam\\nnostrum rerum est autem sunt rem eveniet architecto'
    }
  ]
})

</script>

<template>
  <div>Catalog</div>
</template>
