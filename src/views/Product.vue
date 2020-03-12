<template>
   <div class="product">
      <div class="title"><h1>{{this.prod.product_title}}</h1></div>
      <div class="content" v-if="this.screen_width>=900">
         <div class="pro1" v-for="item in this.prod.product.productList">
            <img :src="require('../assets/'+item.img)" alt="" class="image">
            <div class="down">
               <h4>{{item.title}}</h4>
               <div style="line-height: 1.5;">{{item.content}}</div>
            </div>
            <el-button type="text" class="button" @click="ToGit1(item.url)">源码查看</el-button>
         </div>
      </div>
      <div class="s-content" v-else>
         <div class="pro1" v-for="item in this.prod.product.productList">
            <img :src="require('../assets/'+item.img)" class="image">
            <div class="down">
               <h4>{{item.title}}</h4>
               <div style="line-height: 1.5;">{{item.content}}</div>
            </div>
            <el-button type="text" class="button" @click="ToProductGit(item.url)">源码查看</el-button>
         </div>
      </div>
      <el-link class="link" type="primary" href="https://github.com/Sunzkszk" :underline="false">
         <div>
            <img src="../assets/github.svg" alt="" />
            <span>在我的Github上查看更多项目</span>
         </div>  
      </el-link>
   </div>
</template>
<script>
   import data from '@/data.js';
   export default{
      name:'Product',
      props:{
         value:String,
      },
      watch:{
        value:function(){
           if(this.value=="1"){
              this.prod = data.eng;
           }
           else{
              this.prod= data.cn;
           } 
        } 
      },
      data(){
         return{
            screen_width: document.body.clientWidth,
            prod:data.cn,
         }
      },
      mounted(){
         window.onresize = () => {
           this.screen_width = document.body.clientWidth;
         }
      },
      methods:{
         ToProductGit(url){
            window.location.href = url; 
         },
      },
   }
</script>

<style scoped lang="scss">
   .product{
      height: 90%;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
      .title{
         h1{
            color:#F4F4F4;
         }
      }
      .content{
         height: 100%;
         width: 80%;
         display: flex;
         flex-direction: row;
         justify-content: space-around;
         align-items: center;
         .pro1{
            background-color: white;
            width: 30%;
            height: 90%;
            display: flex;
            flex-direction: column;
            justify-content: flex-start;
            align-items: center;
            padding-top:1%;
            img{
               width: 100%;
               height: 30%;
               padding-bottom: 1%;
            }
            .down{
               height: 60%;
               
               padding-right:2%;
               padding-left:2%;
               padding-bottom:1%;
               
            }
         }
         
      }
      .s-content{
         width: 80%;
         display: flex;
         flex-direction: column;
         justify-content: space-around;
         align-items: center;
         .pro1{
            background-color: white;
            width: 100%;
            height: 30%;
            display: flex;
            flex-direction: row;
            justify-content: space-around;
            align-items: center;
            img{
               height: 100%;
               width: 30%;
               @media screen and (max-width: 800px){
                  height: 50%;
               }
            }
            div{
               height: 100%;
               width: 60%;
               display: flex;
               flex-direction: column;
               justify-content: flex-end;
               align-items: center;
               h4,div{
                  height:100%;
                  width: 100%;
                  @media screen and (max-width: 800px){
                     font-size:0.9rem;
                  }
               }
               
            }
         }
      }
      .link{
         div{
            cursor: pointer;
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: center;
            img{
               width: 8%;
            }
         }
      }
   }
</style>
