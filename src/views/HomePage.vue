<template>
   <div class="homepage">
      <div class="avator"><img :src="require('../assets/'+this.info.avator)" alt="" /></div>
      <h2>{{this.info.sent}}</h2>
      <hr />
      <h3>{{this.info.name}}</h3>
      <h3>{{this.info.degree}}</h3>
      <h3>{{this.info.dream}}</h3>
      <h3>{{this.info.mail}}</h3>
      <div class="contact">
         <img :src="require('../assets/'+this.info.github)" alt="" @click="ToUrl(this.info.github_url)" />
         <img :src="require('../assets/'+this.info.csdn)" alt="" @click="ToUrl(this.info.csdn_url)" />
         <img :src="require('../assets/'+this.info.weibo)" alt="" @click="ToUrl(this.info.weibo_url)" />
      </div>
   </div>
</template>

<script>
   import data from '@/data.js';
   export default{
      name:'HomePage',
      props:{
         value:String,
      },
      watch:{
        value:function(){
           if(this.value=="1"){
              this.info = data.eng;
           }
           else{
              this.info = data.cn;
           } 
        } 
      },
      data(){
         return{
            info:data.cn,
         }
      },
      methods:{
         ToUrl(url){
            window.location.href = url; 
         },
      }
   }
</script>

<style scoped lang="scss">
   .homepage{
      height: 80%;
      width: 100%;
      padding-top:5%;
      display:flex;
      flex-direction:column;
      justify-content: space-around;
      align-items: center;
      .avator{
         margin-bottom: 2%;
         img{
            height:85px;
            border-radius:50%;
         }
      }
      h2,h3{
         @media screen and (max-width: 600px) and (min-width: 450px){
            font-size: 1rem;
         }
         @media screen and (max-width: 450px){
            font-size: 1rem;
         }
      }
      hr{
         height:3px;
         border:none;
         border-top:1px groove #FF8C00;
         width: 80%;
         margin-bottom: 2%;
      }
      .contact{
         width: 60%;
         display:flex;
         flex-direction:row;
         justify-content: space-around;
         align-items: center;
         img{
            cursor: pointer;
            @media screen and (min-width: 600px){
               width:6%;
            }
            @media screen and (max-width: 600px) and (min-width: 450px){
               width:8%;
            }
            @media screen and (max-width: 450px){
               width:14%;
            }
         }
      }
   }
</style>
