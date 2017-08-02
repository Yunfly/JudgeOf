<template>
  <div>
    <div class="judge-modal" @click="cancel"></div>
    <div class="judge">
      <br>
      <div class="text-center font16">评价</div>
      <judge-star v-for="item,index in starList" :key="index" @judge="judge" :name="item.name" :index="index" ></judge-star>
      <br>
      <div class="box container text-left">
        <span class="icon-i"></span>  评价内容
      </div>
      <div class="bgfff container font14">
        <textarea  placeholder="请输入您的评价，方便我们改进，谢谢！" type="textarea" class="textarea" rows="6" v-model="judgeTxt"></textarea>
      </div>
      <div class="container">
        <br>
        <div class="btn btn_block text-center" @click="submit">提交</div>
      </div>
    </div>
  </div>
</template>

<script>
  import JudgeStar from './judgeStar.vue'
  export default{
    data(){
      return{
        starList:[
          {name:'服务态度',key:'evaluate.serviceStarLevel'},
          {name:'责任感',key:'evaluate.dutyStarLevel'},
          {name:'准时度',key:'evaluate.onTimeStarLevel'},
        ],
        evaluate:[],
        judgeTxt:''
      }
    },
    components:{
      JudgeStar
    },
    computed:{

    },
    methods:{
      cancel(){
        this.$emit('cancel')
      },
      submit(){
        let data = '';
        this.starList.forEach((val,index)=>{
          data =`${val.key}:${this.evaluate[index]}`
            console.log(data)
        });
      },
      judge(data){
          this.evaluate[data[0]]=data[1];
      }
    }
  }
</script>

<style scoped>
  .textarea{
      width:100%;
      padding: 10px;
      box-sizing: border-box;
      border-radius: 12px;
      outline: none;
  }
  .box{
    color: #333;
    font-size:14px;
    height:30px;line-height: 30px;
  }
  .icon-i{
    width:3px;
    height: 12px;
    background-color: #ff94a0;
    display:inline-block;
    border-radius: 4px;
  }
  .judge-modal{
    background: rgba(0,0,0,0.5);
    position: fixed;
    width: 100vw;
    height: 100vh;
    z-index:9999;
    bottom: 0;
    left:0;
  }
  .judge{
    position: fixed;
    width: 100vw;
    height: 400px;
    background-color: #fff;
    z-index:9999;
    bottom: 0;
    left:0;
  }
</style>
