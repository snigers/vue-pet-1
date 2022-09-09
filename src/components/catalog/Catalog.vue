<script setup lang="ts">
import styles from './Catalog.module.scss'
import {useCatalogForm} from "@/components/catalog/useCatalogForm";
import {defineProps} from "vue";
import {useQuery} from "vue-query";
import axios from "axios";

const props = defineProps<{
    title: string
  }>()

const { posts, addPost, removePost, value, errorMessage, isLoading} = useCatalogForm(props)


return useQuery('get posts', () =>
    axios.get('https://jsonplaceholder.typicode.com/posts')
)
</script>

<template>
  <div :class="styles.wrapper">
    <h1>Add posts</h1>
    <form>
      <input v-model="value" placeholder="Enter post title" type="text" />
      <div v-if="errorMessage">{{errorMessage}}</div>
      <button @click.prevent="addPost">Add</button>
    </form>

    <div v-if="isLoading">Loading...</div>
    <div v-if="!posts.length">Posts not found!</div>

    <ul>
      <li :key="post.id" v-for="post in posts">
        <span>{{post.id}} - {{post.title}}</span>
        <button @click="removePost(post.id)">X</button>
      </li>
    </ul>
  </div>
</template>
