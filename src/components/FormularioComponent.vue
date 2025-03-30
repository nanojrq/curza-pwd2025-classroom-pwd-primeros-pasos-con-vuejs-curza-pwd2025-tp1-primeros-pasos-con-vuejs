<script setup lang="ts">

import { ref } from 'vue';

const nombre = ref('');
const email = ref('');
const password = ref('');
const fechaNacimiento = ref('');
const edad = ref(''); 


const enviar= ()=> {
    if (nombre.value && email.value && password.value && fechaNacimiento.value) {
        alert(`Nombre: ${nombre.value}, Email: ${email.value}, Contraseña: ${password.value}, Fecha de Nacimiento: ${fechaNacimiento.value}`);
        //limpiar los campos
        nombre.value = '';  
        email.value = '';
        password.value = '';
        calcularEdad(); //calcular la edad
        fechaNacimiento.value = '';
    }  
    else {
        alert('Por favor, completa todos los campos.');
    }
};

const calcularEdad = () => {
    console.log(fechaNacimiento);
    const naciomiento = new Date(fechaNacimiento.value);
    const hoy = new Date();
    let calcular = hoy.getFullYear() - naciomiento.getFullYear();
    const mes = hoy.getMonth() - naciomiento.getMonth();
    if (mes < 0 || (mes === 0 && hoy.getDate() < naciomiento.getDate())) {
        calcular--;
    }
    alert(`Tu edad es: ${calcular}`);
    edad.value = calcular.toString()
    return edad;
};



</script>



<template>
<div class="contenedorform">
    <h1>Registro</h1>
 <input type="text" placeholder="Nombre" v-model="nombre" />
 <input type="email" placeholder="Email" v-model="email" />
 <input type="password" placeholder="Contraseña" v-model="password" />
 <input type="date" placeholder="Fecha de Nacimiento" v-model="fechaNacimiento" />
 <button class="boton" @click="enviar()"> Enviar</button>
    <p>Formulario de Registro </p>
    <p>Nombre: {{ nombre }}</p>
    <p>Email: {{ email }}</p>
    <p>Contraseña: {{ password }}</p>
    <p>Fecha de Nacimiento: {{ fechaNacimiento }}</p>
    <p>Edad: {{ edad }}</p>
</div>



</template>




<style scoped>

.contenedorform {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
}

#input {
  margin: 10px 0;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 300px;
} 

.boton {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 15px;
  font-size: 16px;
}


</style>