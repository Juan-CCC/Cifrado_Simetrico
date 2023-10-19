<template>
  <div class="container">
    <label>Mensaje a cifrar:</label>
    <input v-model="mensaje" />

    <button @click="cifrar">Cifrar</button>
    <p>Mensaje cifrado: {{ mensaje_Cifrado }}</p>

    <button @click="descifrar">Descifrar</button>
    <p>Mensaje descifrado: {{ mensaje_Descifrado }}</p>
  </div>
</template>

<script>
import CryptoJS from "crypto-js";

export default {
  data() {
    return {
      mensaje: "",
      mensaje_Cifrado: "",
      mensaje_Descifrado: "",
      clave: "carlos18",
    };
  },
  methods: {
    cifrar() {
      this.mensaje_Cifrado = CryptoJS.DES.encrypt(this.mensaje, this.clave).toString();
    },
    descifrar() {
      const bytes = CryptoJS.DES.decrypt(this.mensaje_Cifrado, this.clave);
      this.mensaje_Descifrado = bytes.toString(CryptoJS.enc.Utf8);
    },
  },
};
</script>

<style>
.container {
  max-width: 500px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  font-family: sans-serif}

label {
  display: block;
  text-align: center;
  margin-bottom: 10px;
}

input {
  width: 96%;
  padding: 8px;
  margin-bottom: 15px;
}

button {
  margin-left: 40%;
  width: 100px;
  background-color: #4caf50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

p {
  margin-top: 15px;
  text-align: center;
}
</style>
