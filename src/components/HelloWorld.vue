<template>
  <div>
    <div class="Contenedor">
      <div class="centrado">
        <div class="texto">
          <h2>Cifrado escitala</h2>
        </div>
        <div class="uno">
          <textarea name="ci" id="ci" cols="30" rows="10" @input="escribir"></textarea>
          <div class="tres">
            <button @click="cifrar()">Cifrar</button>
            <button @click="descifrar">Descifrar</button>
          </div>
          <textarea name="de" id="de" cols="30" rows="10" v-model="resultado"></textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CryptoJS from 'crypto-js';


export default {
  data() {
    return {
      cifrado: '',
      resultado: '',
      contra: 'Rogelio'
    };
  },
  methods: {
    escribir(event) {
      this.cifrado = event.target.value;
    },
    cifrar() {

    const ciphertext = CryptoJS.AES.encrypt(this.cifrado,this.contra).toString();
     this.resultado= ciphertext;
   
    },
    descifrar() {
      const bytes = CryptoJS.AES.decrypt(this.cifrado, this.contra);
    const originalData = bytes.toString(CryptoJS.enc.Utf8);
    this.resultado= originalData;
      
    },
  },
};
</script>

<style scoped>

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    margin: 0;
    padding: 0;
  }

  .Contenedor {
    background-color: #fff;
    margin: 20px;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }

  .centrado {
    text-align: center;
  }

  .texto {
    margin-bottom: 20px;
  }

  h2 {
    font-size: 28px;
    color: #333;
  }

  .uno textarea {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    resize: none;
  }

  .tres button {
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin: 1%;
  }

  .tres button:hover {
    background-color: #0056b3;
  }

  .tres button:active {
    background-color: #03376e;
  }



</style>
