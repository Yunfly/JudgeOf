<template>
  <div class="flex_cont container">
    <div class="flex_item name">{{name}}</div>
    <div class="flex_item">
      <star-img @choose="choose" v-for="item,index in starArr" :key="index" :chooseIndex="chooseIndex" :index="index"></star-img>
    </div>
  </div>

</template>

<script>
  import StarImg from './starImg.vue'
  export default{
    props:{
      name:String,
      index:''
    },
    data(){
      return{
        chooseIndex:4,
        starArr:Array.from({ length: 5 })
      }
    },
    components:{
      StarImg
    },
    mounted(){
      this.$emit('judge',[this.index,this.chooseIndex+1]);
    },
    methods:{
      choose(data){
        this.chooseIndex = data;
        this.$emit('judge',[this.index,this.chooseIndex+1]);
      }
    }
  }
</script>

<style scoped>
  .name{
    color: #9a9a9a;
    flex: 0 0 60px;
    padding-right: 14px;
    letter-spacing: 1px;
  }
  .container{
    height: 30px;
    line-height: 30px;
  }
  .flex_item img{
    margin:0 2px;
  }
</style>
