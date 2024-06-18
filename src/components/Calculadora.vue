<script setup>
import {reactive } from "vue";   
    const estado = reactive({
    operacao : '+',
    resultado : 0,
    a:0,
    b:0

    })

    const calculaResultado =() =>{
    switch(estado.operacao){
        case '+':
        return soma();
        case '-':
        return subtracao(); 
        case '*':
        return multiplicacao();
        case '/':
        return divisao();      
    }
    }

    function soma(){
    estado.resultado = estado.a + estado.b ;
    }
    function subtracao(){
    estado.resultado = estado.a - estado.b ;
    }
    function multiplicacao(){
    estado.resultado = estado.a * estado.b ;
    }
    function divisao(){
    if (estado.b==0) {
        estado.resultado = "Divisão por zero";      
    }
    else{
        estado.resultado = estado.a / estado.b ;
    }
    }
    

</script>

<template>
    <div class="container">
    <header class="p-4 mb-4 mt-4 rounded-4">
        <h1>Calculadora Aritmética</h1>
    </header>
    <div class="calculadora">
        <form >
        <div class="row">
            <div class="col-md-2">
            <input class="form-control" v-model="estado.a"  @keyup="calculaResultado()" @change="calculaResultado()" type="number" placeholder="insira um número">
        </div>
        <div class="col-md-1">
            <select class="form-control" v-model="estado.operacao" @change="calculaResultado()" >
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
            </select>

        </div>
        <div class="col-md-2">
            <input class="form-control"  v-model="estado.b" @keyup="calculaResultado()" @change="calculaResultado()" type="number" placeholder="insira um número">
        </div>
        <span class="col-md-4 rounded-4 resultado"> {{ estado.resultado }}</span>
        </div>      
        </form>

    </div>
    </div>
</template>

<style scoped>
.container{
    max-width: 700px;
}
header{
    background-color: rgb(236, 236, 236);
}
input, span{
    display: inline;
    font-size: 24px;
    padding-top: 4px;
}
select{
    margin-top: 8px;
    background-color:  rgb(236, 236, 236);
    border: 0cap;
}
.resultado{
    padding-top: 4px;
    padding-right: 16px;
    background-color: rgb(236, 236, 236);
    text-align: end;
}

</style>
