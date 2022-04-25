<template>
  <div class="hello">
    <div class="top">

    <div class="lefttop-text">
      <div class="textone">消费者权益维权自动问答系统</div>
      <div class="texttwo">Consumer Protection</div>
      <div class="textthree">
        <p>在下框中输入您的理由和需要陈述的事实，我们为您提供有力参考</p>
        <p>Enter your reasons and facts in the box below</p>
        <p>We will provide you with a strong reference</p>
      </div>
    </div>

    <div class="right-top">
      <img src="../assets/img/righttop.png" alt="">
    </div>
    </div>
    <!-- 输入框 -->
    <div class="inputbox">
      <textarea type="text" v-model="inputdata"></textarea>
      <button @click="returndata()">Submit</button>
    </div>
    

    <!-- 内容展示 -->
    <div class="displaybox">
      <div class="titlebox">
        <div class="title">
          <img src="../assets/img/icon2.png" alt="">
          <span>Result</span>
        </div>
        <p class="titletext">根据您描述的情况，系统推断可能违反了《消费者权益保护法》的以下条例</p>
      </div>

      <div class="contentbox">
        <div class="content" v-for="(item,value) in data" :key="value">
          <div class="content-title">
            <img src="../assets/img/icon1.png" alt="">
            <span>{{item.laws}}</span>
          </div>
          <div class="content-text">
            {{item.content}}
          </div>
        </div>
      </div>
    </div>

    <div class="footer">
      <img src="../assets/img/footer.png" alt="">
    </div>

  </div>
</template>

<script>
import axios from 'axios';
// import {data} from "../assets/js/data";
export default {
  name: 'HelloWorld',
  data(){
    return{
      data:'',
      inputdata:""
    }
  },
  methods:{
    returndata(){
      console.log(this.inputdata);
      axios({
        url:'http://127.0.0.1/fact',
        method:'post',
        params:{
          fact:this.inputdata
        },
        headers:{
          "Content-Type": "application/x-www-form-urlencoded;charset=utf-8",
        },
        dataType:'json',
      })
      .then((res) =>{
        this.data = res.data.data;
        console.log(res.data.data);
      })
      .catch(function(error){
        console.log("连接失败");
        console.log(error);
      })
    }
  }
}
</script>

<style scoped>
.top{
  display: flex;
  width: 90%;
  justify-content: space-around;
  margin-left: 10%;
}
.lefttop-text{
  margin-top: 8rem;
  width: 60%;
  letter-spacing: 0.1rem;
}
.textone{
  font-size: 3rem;
  font-weight: 300;
  letter-spacing: 0.2rem;
}
.texttwo{
  font-size: 3rem;
  font-weight: 300;
}
.textthree{
  margin-top: 5rem;
  font-size: 1.2rem;
  color: #758595;
}

.right-top{
  width: 40%;
}
.right-top img{
  width: 100%;
  height: 100%;
}

.inputbox{
  width: 55rem;
  margin: 0 auto;
  margin-top: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.inputbox textarea{
  width:100%;
  padding: 0;
  border: 0;
  box-sizing: border-box;
  outline: none;
  height: 25rem;
  background-color:  #3e413f;
  color: #A8ABBC;
  font-size: 1.2rem;
  letter-spacing: 0.1rem;
  padding:1.2rem 2rem;
}

.inputbox button{
  width: 15rem;
  height: 3rem;
  line-height: 3rem;
  font-size: 1.2rem;
  color: #4a59ff;
  border: 0;
  background-color: white;
  margin-top: 2rem;
  outline: none;
  cursor: pointer;
}

.displaybox{
  width: 70rem;
  margin: 0 auto;
  margin-top: 10rem;
}
.titlebox{
  width: 100%;
  text-align: center;
}
.title{
  letter-spacing: 0.5rem;
}
.title img{
  width: 3rem;
}
.title span{
  font-size: 2.5rem;
  vertical-align: top;
}
.titletext{
  color: azure;
  letter-spacing: 0.1rem;
}

.contentbox{
  width: 100%;
  margin-top: 5rem;
}
.content{
  width: 100%;
  background-color: #3e413f;
  box-sizing: border-box;
  padding: 2rem;
  margin-top: 2rem;
}
.content-title{
  width: 100%;
}
.content-title img{
  width: 5rem;
  height: 5rem;
  display: inline-block;
}
.content-title span{
  line-height: 5rem;
  vertical-align:top;
  font-size: 1.5rem;
  margin-left: 1rem;
}
.content-text{
  width:100%;
  box-sizing: border-box;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  letter-spacing: 0.1rem;
}

.footer{
  width: 100%;
  /* height: 20rem; */
}
.footer img{
  width: 100%;
  height: 25rem;
}
</style>
