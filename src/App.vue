<template>
<div id="app">
  
  <h1>Math Quiz App</h1>
  <OperatorQuiz @onBack="clearOperator" v-if="operator" :operator="operator"/>
  <OperatorSelector v-if="!operator" @changeOperator="changeOperator"/>
    
</div>
</template> 

<script>
import OperatorSelector from './components/OperatorSelector.vue';
import OperatorQuiz from './components/OperatorQuiz.vue';

export default {
    name: 'App',
    data () {
      return {
        operator: null,
      };
    },
    methods:{
      changeOperator(operator){
        this.operator = operator;
      },
      clearOperator(){
        this.operator = null ;
      }
    },
    components: { OperatorSelector ,OperatorQuiz}
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    background: rgb(171, 85, 85);
}

button {
    background: red;
    padding: 10px;
    width: 150px;
    height: 100px;
    color: white;
    font-size: medium;
    cursor: cell;
    margin: 20px;
    border-radius: 10px;
}

button:hover {
    background-color: #4CAF50;
    color: white;
}
</style>
