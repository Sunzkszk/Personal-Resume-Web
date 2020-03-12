<template>
   <div class="home">
      <div class="language">
         <h3>中&nbsp;</h3>
            <el-switch v-model="value" active-color="#ff4949" inactive-color="#13ce66"
               active-value="1" inactive-value="0">
            </el-switch>
         <h3>&nbsp;英</h3>
      </div>
      <ul>
         <li v-for="item in this.title.titleList">
            <el-tooltip effect="dark" :content="item.title" placement="left">
               <em v-on:click="directToPage(item.index)">
                  <img :src="item.svg" alt="" />
               </em>
            </el-tooltip> 
         </li>
      </ul>
      <full-page :options="options" id="fullpage" style="height: 100%;margin:0;">
         <div class="section" style="height: 100%;">
            <HomePage :value="this.value" />
         </div>
         <div class="section">
            <SelfIntro :value="this.value" />
         </div>
         <div class="section">
            <Skill :value="this.value" />
         </div>
         <div class="section">
            <Product :value="this.value" />
         </div>
         <div class="section">
            <Blog :value="this.value" />
         </div>
      </full-page>
      <div class="pulldown" @click="PullDown()">
         <img src="../assets/jiantou.png" alt="" />
      </div>
   </div> 
</template>

<script>
import HomePage from '@/views/HomePage.vue'
import Blog from '@/views/Blog.vue'
import Product from '@/views/Product.vue'
import SelfIntro from '@/views/SelfIntro.vue'
import Skill from '@/views/Skill.vue'
import data from '@/data.js';
export default {
   name: 'Home',
   components: {
      HomePage,
      Blog,
      Product,
      SelfIntro,
      Skill,
   },
   watch:{
     value:function(){
        if(this.value=="1"){
           this.title = data.eng;
        }
        else{
           this.title = data.cn;
        } 
     } 
   },
   data () {
      return {
         value: '0',
         currentPage:1,
         endPage:0,
         height : document.documentElement.clientHeight || document.body.clientHeight,
         options: {
            licenseKey: 'YOUR_KEY_HERE',
            afterLoad: this.afterLoad,
            scrollOverflow: true,
            scrollBar: false,
            menu: '#menu',
            navigation: true,
            anchors: ['page1', 'page2', 'page3', 'page4', 'page5', 'page6'],
            sectionsColor: ['#F7F7F7', '#516395', '#FF9D70', '#7C8990', '#A19870', '#86AFA4', '#E0E3DA']
         },
         title: data.cn,
      }
   },
   mounted(){
         console.log('Hi! 朋友，感谢您愿意调试网站代码。');
         console.log('目前网站仍处于完善阶段，有兴趣或者建议的小伙伴们通过网站中我的邮箱联系我吧~');
         console.log('本网站源码已开源在我的Github上，任何问题请提issue,喜欢请点个star吧！');
   },
   methods:{
      directToPage(index){
         if(window.location.hash != '#page'+index){
            this.currentPage = index;
           
         }
         fullpage_api.moveTo('page'+index);
         
      },
      PullDown(){
       fullpage_api.moveSectionDown();
      },
      
   }
}
</script>

<style scoped lang="scss">
   .home{
      height: 100%;
      margin: 0;
      padding:0;
      .language{
         width: 10%;
         display: flex;
         flex-direction: row;
         justify-content: space-around;
         align-items: center;
         position: absolute;
         right: 8%;
         top:4%;
         z-index:1;
         h3{
            font-size: 1rem;
         }
            
      }
      ul{
         position: absolute;
         right: 2%;
         top: 30%;
         z-index:1;
         height: 100%;
         li{
            height:10%;
            width: 10%;
            list-style: none;
            img{
               height:25px;
               border-radius:50%;
               //opacity: 0;
            }
            :hover{
               transform: translateY(-50%) scale(1.6);
               opacity: 1;
               cursor: pointer;
            }
         }
      }
      .pulldown{
         margin:0;
         padding:0;
         :hover{
            transform: translateY(-50%) scale(1.2);
            opacity: 1;
            cursor: pointer;
         }
         position: absolute;
         bottom: 0;
         left: 50%;
         margin-left: -15px;
         z-index:1;
         img{
            height:30px;
         }
      }
   }
</style>