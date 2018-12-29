<template>
  <div class="row"> 
    <div class="col-md-6 col-md-offset-3">
       <form id="transForm" class="well form-inline" @submit.prevent="sendTransLetter">
          <input type="text" class="form-control" placeholder="请输入要翻译的内容" v-model="transText">
           <select v-model="language" class="form-control">
             <option value="en">English</option>
             <option value="ko">Korean</option>
             <option value="ru">Russan</option>
             <option value="ja">Janpenese</option>
           </select>
             <input class="btn btn-primary" type="submit" value="翻译">
       </form>


    </div>
 
  </div>
</template>

<script>
export default {
  name: 'transLatePut',
  data () {
    return {
      transText:"",
      language:""
    }
  },
  methods:{
    sendTransLetter (e) {
      e.preventDefault;
      this.$emit('transText',this.transText,this.language)
    }
  },
  created(){
    this.language='en'
  }  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
   #transForm{
      border:1px solid #ccc;
      border-radius:10px;
   }
</style>
