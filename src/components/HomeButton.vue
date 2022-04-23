<template>
  <button @click="onClick" :class="[color]">{{title}}</button>
</template>

<script>
export default {
    name: "HomeButton",
    props : {
        title : String,
        color : String
    },
    methods: {
        onClick(){
            this.$emit("btn-click")
        }
    }
}
</script>

<style>
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

</style>