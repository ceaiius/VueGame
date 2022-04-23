<template>
  <div class="app">
    <div class="headerDiv">
      <h1>YOU</h1>
      <h1>MONSTER</h1>
    </div>
    <div class="healthDiv">
      <h2>{{myHealth}}</h2>
      <h2>{{monsterHealth}}</h2>
    </div>
    <div class="btnDiv">
      <HomeButton @btn-click="attackMethod" title="ATTACK" color="style-1"/>
      <HomeButton @btn-click="specialAttackMethod" title = "SPECIAL ATTACK" color="style-2"/>
      <HomeButton @btn-click="healMethod" title="HEAL" color="style-3"/>
      <HomeButton @btn-click="giveUpMethod" title="GIVE UP" color="style-4"/>
     
    </div>

    <div v-if="lostEnabled" id="loserDiv">
      <h1>YOU LOST PUSSY 💋</h1>
    </div>
    <div v-if="wonEnabled" id="winnerDiv">
      <h1>AYE CONGRATS DAWG YOU DA REAL ONE ⛷️ </h1>
    </div>
  </div>

</template>

<script>

import HomeButton from "./components/HomeButton.vue"

export default {
  name: 'App',
  data() {
    return {
      myHealth: 100,
      monsterHealth: 100,
      lostEnabled:false,
      wonEnabled: false
    }
  },
  components:{
    HomeButton
  },
  methods: {
    attackMethod(){
      const randomYou = Math.floor(Math.random() * 5) + 1;
      this.myHealth -= randomYou
      
      const randomMonster = Math.floor(Math.random() * 8) + 1;
      this.monsterHealth -= randomMonster;

      if(this.myHealth <=0 || this.monsterHealth <=0){
       
        this.myHealth = 100;
        this.monsterHealth = 100;
        this.wonEnabled = true;
        setTimeout(()=>{
       this.wonEnabled = false;
      }, 3000)
      }
    },
    specialAttackMethod(){
      const randomYou = Math.floor(Math.random() * 5) + 3;
      const randomMonster = Math.floor(Math.random() * 10) + 3;
      this.myHealth -= randomYou;
      this.monsterHealth -= randomMonster;
      if(this.myHealth <=0 || this.monsterHealth <=0){
        
        this.myHealth = 100;
        this.monsterHealth = 100;
        this.wonEnabled = true;
        setTimeout(()=>{
       this.wonEnabled = false;
      }, 3000)
      }
    },
    healMethod(){
       const randomYou = Math.floor(Math.random() * 3) + 1;
       if(this.myHealth<100){
       this.myHealth += randomYou;
       if(this.myHealth>100){
         this.myHealth = 100;
       }
       }
    },
    giveUpMethod(){
      
      this.myHealth = 100;
      this.monsterHealth = 100;
      this.lostEnabled = true;
      setTimeout(()=>{
       this.lostEnabled = false;
      }, 3000)
    }
  }
  
}
</script>

<style >
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  background-color: #5534A5;
}

.headerDiv{
  display: flex;
  justify-content: center;
  padding-top: 4%;
  gap: 20%;
}
.healthDiv{
  display: flex;
  justify-content: center;
  padding-top: 4%;
  gap: 25%;
}

h1{
  color:#FF6FB5;
  font-family: 'Cinzel', serif;
}
h2{
  color:#B4FF9F;
  font-family: 'Cinzel', serif;
}


#loserDiv{
  display: flex;
  justify-content: center;
  padding-top: 5%;
  font-size: 40px;
  color: #827397;
}
#loserDiv h1{
  color: #EF6D6D;
}
#winnerDiv{
  display: flex;
  justify-content: center;
  padding-top: 5%;
  font-size: 40px;
  color: #827397;
}
#winnerDiv h1{
  color: #EF6D6D;
}
</style>

 



