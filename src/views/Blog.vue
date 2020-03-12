<template>
   <div class="blog">
      <div class="title"><h1>{{this.blog.blog_title}}</h1></div>
      <div class="content">
         <div class="left">
            <div class="card" v-for="item in this.blog.blog.blog_left">
               <div class="title">
                  <span @click="ToAtricle(item.url)" style="cursor: pointer;">{{item.title}}</span>
               </div>
               <div class="page">
                  <span @click="ToAtricle(item.url)" style="line-height: 1.5;cursor: pointer;">{{item.content}}</span>  
               </div>
               <div class="date">
                  <img src="../assets/icon--date.png" alt=" " />
                  <span>{{item.date}}</span>
               </div>
            </div>
         </div>
         <div class="right">
            <div class="card" v-for="item in this.blog.blog.blog_right">
               <div class="title">
                  <span @click="ToAtricle(item.url)" style="cursor: pointer;">{{item.title}}</span>
               </div>
               <div class="page">
                  <span @click="ToAtricle(item.url)" style="line-height: 1.5;cursor: pointer;">{{item.content}}</span>  
               </div>
               <div class="date">
                  <img src="../assets/icon--date.png" alt=" " />
                  <span>{{item.date}}</span>
               </div>
            </div>
         </div>
      </div>
   </div>
</template>

<script>
   import data from '@/data.js';
   export default{
      name:'Blog',
      props:{
         value:String,
      },
      watch:{
        value:function(){
           if(this.value=="1"){
              this.blog = data.eng;
           }
           else{
              this.blog = data.cn;
           } 
        } 
      },
      data(){
         return{
            blog:data.cn,
         }
      },
      methods:{
         ToAtricle(url){
            window.location.href = url;
         }
      }
   }
</script>

<style scoped lang="scss">
   .blog{
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
         width: 90%;
         height: 90%;
         display: flex;
         flex-direction: row;
         justify-content: space-around;
         align-items: center;
         .left,.right{
            width: 45%;
            height:100%;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
            .card{
               width:100%;
               @media screen and (max-width: 600px){
                  width:96%;
               }
               height:30%;
               border-radius: 2%;
               background-color:white;
               border:1px solid #004444;
               display: flex;
               flex-direction: column;
               justify-content: space-around;
               align-items: flex-start;
               padding-left:1%;
               .title{
                  width:100%;
                  height:30%;
                  span{
                     font-weight: bold;
                     @media screen and (min-width: 1000px){
                        font-size: 1.4rem;
                     }
                     @media screen and (max-width: 1000px) and (min-width: 800px){
                        font-size: 1.2rem;
                     }
                     @media screen and (max-width: 800px) and (min-width: 600px){
                        font-size: 1.0rem;
                     }
                     @media screen and (max-width: 600px){
                        font-size: 0.8rem;
                     }
                  }
               }
               .page{
                  width:100%;
                  height:50%;
                  @media screen and (min-width: 800px){
                     font-size: 1.0rem;
                  }
                  @media screen and (max-width: 800px) and (min-width: 600px){
                     font-size: 0.9rem;
                  }
                  @media screen and (max-width: 600px) and (min-width: 500px){
                     font-size: 0.8rem;
                  }
                  @media screen and (max-width: 500px){
                     font-size: 0.6rem;
                  }
               }
               .date{
                  width:100%;
                  height:20%;
                  display: flex;
                  flex-direction: row;
                  justify-content: flex-start;
                  align-items: center;
                  span{
                     @media screen and (max-width: 800px) and (min-width: 600px){
                        font-size: 0.9rem;
                     }
                     @media screen and (max-width: 600px) and (min-width: 500px){
                        font-size: 0.7rem;
                     }
                     @media screen and (max-width: 500px){
                        font-size: 0.6rem;
                     }
                  }
                  img{
                     padding-right: 2%;
                     @media screen and (min-width: 1000px){
                        width:5%;
                     }
                     @media screen and (max-width: 1000px) and (min-width: 800px){
                        width:6%;
                     }
                     @media screen and (max-width: 800px) and (min-width: 600px){
                        width:7%;
                     }
                     @media screen and (max-width: 600px) and (min-width: 500px){
                        width:8%;
                     }
                     @media screen and (max-width: 500px){
                        width:10%;
                     }
                  }
               }
            }
         }
      }
   }
</style>
