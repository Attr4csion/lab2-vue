<template>
<div id="app" class="container">
  <div class="menu-bar">
    <button><a @click="nameComp = 'One'">Задание 1</a></button>
    <button><a @click="nameComp = 'Two'">Задание 2</a></button>    
    <button><a @click="nameComp = 'Three'">Задание 3</a></button>    
    <button><a @click="nameComp = 'Four'">Задание 4</a></button>
    <button><a @click="nameComp = 'Five'">Задание 5</a></button>

    <!-- <div v-for="(item,index) in items" :key="index">
      <li :class="{active:checking[index]}">
        <a :href="item.url" @click="checkNav(index)" :class="{activeTo:checking[index]}">{{ item.task }}</a>
      </li>
    </div> -->
  </div>
  <keep-alive>
    <component :is="changeComp"></component>
  </keep-alive>
</div>    
<!-- <router-view class="cont_item"></router-view> -->
</template>


<script>
import ComponentFive from './components/ComponentFive.vue'
import ComponentFour from './components/ComponentFour.vue'
import ComponentOne from './components/ComponentOne.vue'
import ComponentThree from './components/ComponentThree.vue'
import ComponentTwo from './components/ComponentTwo.vue'



export default {
    name:'App',
    data(){
      return{
        nameComp:'One'
        // items:[
        //   {url:'#/one',task:'Задание 1'},
        //   {url:'#/two',task:'Задание 2'},
        //   {url:'#/three',task:'Задание 3'},
        //   {url:'#/four',task:'Задание 4'},
        //   {url:'#/five',task:'Задание 5'}

        // ],
        // checking:[]
      }
    },
    components:{
        ComponentOne,ComponentTwo,ComponentThree, ComponentFour,ComponentFive       
       },
        computed:{
          changeComp(){
            return "Component" + this.nameComp
          }
        },
    methods:{
      // checkNav(index){
      //   for(let i = 0; i < this.items.length;i++){
      //     this.checking[i] = false
      //   }
      //   this.checking[index] = true
      // }
    }
    }
 </script>


 <style>
 * {
    box-sizing: border-box;
    margin: 0;
 }
 #app{
    font-family: 'Roboto', sans-serif;
    font-size: 24px;
    
 }
.container{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    min-width: 600px;
    margin-top: 0 auto;
    align-items: center;
}
.cont_item{
    /* border:3px solid  #ae0; */
    border-radius: 10px;
    padding: 20px;
    margin-top: 50px;
}
.cont_item h1{
text-align: center;}

body {
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
}

.menu-bar  {
  display: flex;
}
.menu-bar button {
 display: inline-block ;
 padding: 10px;
 border: 1px solid black;
}
.menu-bar a{
    text-decoration: none ;
    color: black;

}
.menu-bar button:hover {
  background-color: #ae0; 

}

.active{
  color: black;
  background-color: #ae0; 

}
.activeTo{
  color:black
}
</style>