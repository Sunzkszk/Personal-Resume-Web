<template>
   <div class="skill">
      <div class="title"><h1>{{this.skill.skill_title}}</h1></div>
      <div class="content" v-if="this.screenWidth>=600">
         <div class="top">
            <img :src="require('../assets/'+this.skill.skill_icon.html)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.javascript)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.css)" alt="" />       
            <img :src="require('../assets/'+this.skill.skill_icon.react)" alt="" />           
         </div>
         <div class="bottom">
            <img :src="require('../assets/'+this.skill.skill_icon.vue)" alt="" />          
            <img :src="require('../assets/'+this.skill.skill_icon.nodejs)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.mongodb)" alt="" />            
            <img :src="require('../assets/'+this.skill.skill_icon.sql)" alt="" />          
         </div>
      </div>
      <div class="s-content" v-else>
         <div class="one">
            <img :src="require('../assets/'+this.skill.skill_icon.html)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.javascript)" alt="" />
         </div>
         <div class="two">
            <img :src="require('../assets/'+this.skill.skill_icon.css)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.react)" alt="" />           
         </div>
         <div class="three">
            <img :src="require('../assets/'+this.skill.skill_icon.vue)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.nodejs)" alt="" />              
         </div>
         <div class="four">
            <img :src="require('../assets/'+this.skill.skill_icon.mongodb)" alt="" />
            <img :src="require('../assets/'+this.skill.skill_icon.sql)" alt="" />          
         </div>
      </div>
   </div>
</template>

<script>
   import data from '@/data.js';
   export default{
      name:'Skill',
      props:{
         value:String,
      },
      watch:{
        value:function(){
           if(this.value=="1"){
              this.skill = data.eng;
           }
           else{
              this.skill = data.cn;
           } 
        } 
      },
      data(){
         return{
            skill : data.cn,
            screenWidth: document.body.clientWidth,
         }
      },
      mounted(){
         window.onresize = () => {
           this.screenWidth = document.body.clientWidth;
         }
      },
   }
</script>

<style scoped lang="scss">
   .skill{
      height: 90%;
      width:100%;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      .title{
         h1{
            color:#F4F4F4;
         }
      }
      .content{
         width:80%;
         height: 80%;
         display: flex;
         flex-direction: column;
         justify-content: space-around;
         align-items: center;
         .top,.bottom{
            width:100%;
            height:40%;
            display:flex;
            flex-direction: row;
            justify-content: space-around;
            align-items: center;
            img{
               width: 20%;
            }
         }
      }
      .s-content{
         width:80%;
         height: 80%;
         display: flex;
         flex-direction: column;
         justify-content: space-around;
         align-items: center;
         .one,.two,.three,.four{
            height:20%;
            display:flex;
            flex-direction: row;
            justify-content: space-around;
            align-items: center;
            img{
               width: 25%;
            }
         }
      }
   }
</style>
