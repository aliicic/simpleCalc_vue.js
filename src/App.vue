<template>

<main>
  <input type="text" v-model="CurrentNumber">
  <div class='keys'>
    <button class='op__key'  @click="clearNumber">C</button>
    <button class='op__key'  @click="PlusMinusNumber">+/-</button>
    <button class='op__key'  @click="operationKey('%')">%</button>
    <button class='op__key'  @click="operationKey('/')">/</button>
    <button class='num__key' @click="addNumber(7)">7</button>
    <button class='num__key' @click="addNumber(8)">8</button>
    <button class='num__key' @click="addNumber(9)">9</button>
    <button class='op__key'  @click="operationKey('*')">x</button>
    <button class='num__key' @click="addNumber(4)" >4</button>
    <button class='num__key' @click="addNumber(5)" >5</button>
    <button class='num__key' @click="addNumber(6)" >6</button>
    <button class='op__key'  @click="operationKey('-')">-</button>
    <button class='num__key' @click="addNumber(1)">1</button>
    <button class='num__key' @click="addNumber(2)">2</button >
    <button class='num__key' @click="addNumber(3)">3</button>
    <button class='op__key'  @click="operationKey('+')">+</button>
    <button class='op__key' @click="backSpace" >&lt;</button>
    <button class='num__key' @click="addNumber(0)" >0</button>
    <button class='num__key' @click="addDot">.</button>
    <button class='eq__key' @click="equal">=</button>
    
  </div>
</main>

</template>

<script>


export default {
  name: 'App',

  data : () => ({
     
      CurrentNumber  : '',
      operation : '',
      DotChecker:""


  }),

  methods: {
  addNumber(number){

      if(this.CurrentNumber == 0 && number === 0) return ;
      
      this.CurrentNumber += number ;

    },

  clearNumber(){
      
       this.CurrentNumber = ''

  },

  addDot(){
      
       if (this.CurrentNumber.includes('.')){
  
          if (this.DotChecker == 1){
                 this.CurrentNumber += '.'
                 this.DotChecker = 0 ;
          }else{ return ;}
      
      }else{
        
        this.CurrentNumber += '.'   
      
      }
             
               

  },
  PlusMinusNumber(){
     
     if(parseFloat(this.CurrentNumber) > 0 ){
    
       this.CurrentNumber = '-' + this.CurrentNumber;

     } else {
      this.CurrentNumber =  this.CurrentNumber.substring(1)
     
     }

  },
  operationKey(operation){
   
   
   
  //  this.perviusNumber.push(this.CurrentNumber) ; 
   this.CurrentNumber += operation;
   this.DotChecker = 1;

  //  this.perviusNumber.push(operation) ; 
   this.operation = operation;
   
   

  },

  equal (){

    // switch  (this.operation) {

    //    case  '+' :
    //    this.CurrentNumber =  parseFloat(this.perviusNumber) + parseFloat(this.CurrentNumber);
    //    break;
    //    case  '-' :
    //    this.CurrentNumber =  parseFloat(this.perviusNumber) - parseFloat(this.CurrentNumber)
    //    break;
    //    case  '*' :
    //    this.CurrentNumber =  parseFloat(this.perviusNumber) * parseFloat(this.CurrentNumber)
    //    break;
    //    case  '/' :
    //    this.CurrentNumber =  parseFloat(this.perviusNumber) / parseFloat(this.CurrentNumber)
    //    break;
    //    case  '%' :
    //    this.CurrentNumber =  parseFloat(this.perviusNumber) % parseFloat(this.CurrentNumber)
    //    break;
    // }
    //    this.CurrentNumber = this.CurrentNumber.toString();

     this.CurrentNumber =  eval(this.CurrentNumber).toFixed(2).toString();
    


  },
  backSpace(){
      
    this.CurrentNumber =  this.CurrentNumber.substring( 0 , this.CurrentNumber.length - 1)
       
  }
  
  



     
  },


}
</script>


