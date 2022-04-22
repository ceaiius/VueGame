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
      <button @click="attackMethod" class="style-1">ATTACK</button>
      <button @click="specialAttackMethod" class="style-2">SPECIAL ATTACK</button>
      <button @click="healMethod" class="style-3">HEAL</button>
      <button @click="giveUpMethod"  class="style-4">GIVE UP</button>
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

.btnDiv{
  display: flex;
  justify-content: center;
  padding-top: 4%;
  gap: 3%;
} 

button {
    font-size: 20px;
    background-color: #FF6FB5;
    padding: 12px;
    box-shadow: 0 1px 1px black;
    margin: 10px;
    font-family: 'Cinzel', serif;
}
.style-2{
    background-color: #C74B50;
}

.style-3{
  background-color: #55D8C1;
}

.style-4{
  background-color: #D49B54
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

 



