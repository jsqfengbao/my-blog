<template>
  <div id="add-blog">
    <h1>添加博客</h1>
    <form action="" v-if="!submited">
      <label>博客标题</label>
      <input type="text" v-model="blog.title" required>
      <label>博客内容</label>
      <textarea v-model="blog.content"></textarea>

      <div id="checkboxes">
        <label>Vue.js</label>
        <input type="checkbox" value="Vue.js" v-model="blog.categories">
        <label>Node.js</label>
        <input type="checkbox" value="Node.js" v-model="blog.categories">
        <label>React.js</label>
        <input type="checkbox" value="React.js" v-model="blog.categories">
        <label>Angular4</label>
        <input type="checkbox" value="Angular4" v-model="blog.categories">
      </div>
      <label>作者</label>
      <select v-model="blog.author">
        <option v-for="author in authors">{{author}}</option>
      </select>
      <button v-on:click.prevent="post">添加博客</button>
    </form>

    <div v-if="submited">
      <h3>您的博客发布成功!</h3>
    </div>
    <hr/>
    <div id="preview">
      <h3>博客总览</h3>
      <p>博客标题:{{blog.title}}</p>
      <p>博客内容:</p>
      <p>{{blog.content}}</p>
      <p>博客分类</p>
      <ul>
        <li v-for="category in blog.categories">{{category}}</li>
      </ul>
      <p>作者： {{blog.author}}</p>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
    export default {
      name: "add-blog",
      data () {
          return {
            blog: {
              title: '',
              content: '',
              categories: [],
              author: ''
            },
            authors: ['helah','king','dk'],
            submited: false
          }
      },
      methods: {
        post: function () {
          this.$http.post("http://jsonplaceholder.typicode.com/posts",{
            title: this.blog.title,
            body: this.blog.content,
            userId: 1
          }).then(function(data){
            console.log(data);
            this.submited = true
          })
        }
      }
    }
</script>

<style scoped>

</style>
