<template>
   <div class="selfintro">
      <h1>{{this.self.selfintro_title}}</h1>
      <div class="intro"><h3>{{this.self.self_intro.sub}}</h3></div>
      <div class="basis" v-if="this.screenWidth>=600">
         <div class="top">
            <div class="bir"><img :src="require('../assets/'+this.self.self_intro.bir)" alt="" /><p>{{this.self.bir}}</p></div>
            <div class="school"><img :src="require('../assets/'+this.self.self_intro.school)" alt="" /><p>{{this.self.school}}</p></div>
            <div class="city"><img :src="require('../assets/'+this.self.self_intro.city)" alt="" /><p>{{this.self.city}}</p></div>
         </div>
         <div class="down">
            <div class="mail"><img :src="require('../assets/'+this.self.self_intro.mail)" alt="" /><p>{{this.self.mail}}</p></div>
            <div class="phone"><img :src="require('../assets/'+this.self.self_intro.phone)" alt="" /><p>{{this.self.phone}}</p></div>
            <div class="home"><img :src="require('../assets/'+this.self.self_intro.home)" alt="" /><p>{{this.self.home}}</p></div>
         </div>
      </div>
      <div class="small-basis" v-else>
         <div class="bir"><img :src="require('../assets/'+this.self.self_intro.bir)" alt="" /><p>{{this.self.bir}}</p></div>
         <div class="school"><img :src="require('../assets/'+this.self.self_intro.school)" alt="" /><p>{{this.self.school}}</p></div>
         <div class="city"><img :src="require('../assets/'+this.self.self_intro.city)" alt="" /><p>{{this.self.city}}</p></div>
         <div class="mail"><img :src="require('../assets/'+this.self.self_intro.mail)" alt="" /><p>{{this.self.mail}}</p></div>
         <div class="phone"><img :src="require('../assets/'+this.self.self_intro.phone)" alt="" /><p>{{this.self.phone}}</p></div>
         <div class="home"><img :src="require('../assets/'+this.self.self_intro.home)" alt="" /><p>{{this.self.home}}</p></div>
      </div>
   </div>
</template>

<script>
   import data from '@/data.js';
   export default{
      name:'SelfIntro',
      props:{
         value:String,
      },
      watch:{
        value:function(){
           if(this.value=="1"){
              this.self = data.eng;
           }
           else{
              this.self = data.cn;
           } 
        } 
      },
      data(){
         return{
            self:data.cn,
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
   .selfintro{
      height: 90%;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
      h1{
         color:#F4F4F4;
      }
      .intro{
         width:60%;
         height:20%;
         background-color: #F4F4F4;
         border-radius: 1%;
         display: flex;
         flex-direction: column;
         justify-content: space-around;
         align-items: center;
         h3{
            @media screen and (max-width: 600px) and (min-width: 450px){
               font-size: 1rem;
               line-height:2.5;
            }
            @media screen and (max-width: 450px){
               font-size: 0.9rem;
               line-height:2.5;
            }
         }
      }
      .basis{
         width:60%;
         height:40%;
         background-color: #F4F4F4;
         border-radius: 1%;
         .top,.down{
            width:100%;
            height:50%;
            display:flex;
            flex-direction:row;
            justify-content: space-around;
            align-items: center;
            .bir,.school,.city,.mail,.phone,.home{
               width:30%;
               height:80%;
               display:flex;
               flex-direction:column;
               justify-content: space-around;
               align-items: center;
               img{height:50%;}
               p{
                  @media screen and (max-width: 800px) and (min-width: 600px){
                     font-size:0.6rem;
                  }
                  @media screen and (max-width: 600px) and (min-width: 450px){
                     font-size:0.6rem;
                  }
                  @media screen and (max-width: 450px){
                     font-size:0.1rem;
                  }
               }
            }
         } 
      }
      .small-basis{
         width:60%;
         height:60%;
         background-color: #F4F4F4;
         border-radius: 1%;
         display:flex;
         flex-direction:column;
         justify-content: space-around;
         align-items: center;
         .bir,.school,.city,.mail,.phone,.home{
            width:100%;
            height:17%;
            display:flex;
            flex-direction:row;
            justify-content: flex-start;
            align-items: center;
            img{height:50%;padding-right: 5%;}
         }
      }
   }
   
</style>
