<template>
  <i style="margin: 0 3px;" :class="icon" @click="choose"></i>
</template>

<script>
export default{
    props:{
      index:Number,
      chooseIndex:Number
    },
    data(){
        return{
            icon:'icon-star'
        }
    },
    watch:{
      chooseIndex:function () {
        if(this.chooseIndex>=this.index){
            this.icon = 'icon-star'
        } else {
          this.icon = 'icon-star2'
        }
      },
    },
    methods:{
      choose(){
          /*所选星星最大索引*/
          this.$emit('choose',this.index)
      }
    },
  created(){

  }
}
</script>

<style>
  .icon-star{
    color: #f5e265;
    font-size:20px;
    line-height:30px;
  }
  .icon-star2{
    font-size:20px;
    color: #bbb;
    line-height:30px;
  }
</style>
<style scoped>

</style>
