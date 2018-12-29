<template>
  <div id="app">
      <h4>在线翻译-姚东辉自己的翻译</h4>
       <h5 class="text-muted">简单/高效/便捷</h5>
     <trans-late-put @transText="receiveTransText"></trans-late-put>
     <receive-trans-text v-text="transResult"></receive-trans-text>
  </div>
</template>

<script>
import transLatePut from './components/transLatePut';
import receiveTransText from './components/receiveTransText'

export default {
  name: 'App',
  data () {
    return {
      transResult:''
    }
  },
  components: {
    transLatePut,
    receiveTransText
  },
  methods:{
    receiveTransText (letter,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170721T082515Z.54cf3dc583f679db.f4a96182281281d8b5dfe24b4e88298e2133f219&lang='+language+'&text='+letter)
      .then((response)=>{this.transResult=response.body.text[0]})
    }
  },

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
