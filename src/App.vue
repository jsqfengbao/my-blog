<template>
  <div id="app">
    <BlogHeader></BlogHeader>
    <!--<ShowBlogs></ShowBlogs>-->
    <router-view></router-view>
  </div>
</template>

<script>
import AddBlog from "./components/AddBlog";
import ShowBlogs from './components/ShowBlogs'
import BlogHeader from "./components/BlogHeader";

export default {
  name: 'App',
  components: {
    BlogHeader,AddBlog,ShowBlogs
  }
}
</script>

<style>

</style>
