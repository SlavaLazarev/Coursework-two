<template>
  <div class="container column">
    <form class="card card-w30" @submit.prevent="subHandler">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>
      <div class="form-control">
        <label for="value">Значение</label>
        <textarea 
        id="value" 
        rows="3"
        v-model.trim="val"></textarea>
      </div>
      <button class="btn primary" :disabled="val.length < 4">Добавить</button>
    </form>
    <div class="card card-w70">
    <div v-if="titles.length > 0 ">
    
    <app-title :titles="titles"></app-title>
    
    <app-subtitle :subtitles="subtitles"></app-subtitle>
    
    <app-avatar :avatars="avatars"></app-avatar>
    
    <app-text :texts="texts" ></app-text>
    </div>
     <h3 v-else>ничего нет</h3>
    </div>
  </div>
  <app-loader v-if="loading"></app-loader>
  
  <app-comments 
  v-else
  :comment="comment"
  @load="loadComment"
  ></app-comments>
</template>

<script>
  import axios from 'axios'
  import AppComments from './AppComments'
  import AppTitle from './AppTitle'
  import AppSubtitle from './AppSubtitle'
  import AppAvatar from './AppAvatar'
  import AppText from './AppText'
  import AppLoader from './AppLoader'

export default {

  data() {
    return {
      type: 'title',
      val: '',
      titles: [],
      subtitles: [],
      avatars: [],
      texts: [],
      comment: [],
      loading: false
    }
  },
  methods: {
    async loadComment() {
      this.loading = true
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      const comments = Object.keys(data).map(key => {
        return {
          id: key,
          name: data[key].name,
          body: data[key].body,
          email: data[key].email
        }
      })
      this.comment = comments
      this.loading = false
    },
    subHandler() {
      if (this.type === 'title'){
      this.titles.push({
        titles: this.val
      })} else if (this.type === 'subtitle'){
         this.subtitles.push({
          subtitles: this.val
      })} else if (this.type === 'avatar'){
        this.avatars.push({
          avatars: this.val
      })}else if (this.type === 'text'){
        this.texts.push({
          texts: this.val
      })} this.val = '', this.type = 'title'
      console.log(this.type)
        }
  },
  components: {AppComments, AppTitle, AppSubtitle, AppAvatar, AppText, AppLoader}
}
</script>

<style>
 
</style>
