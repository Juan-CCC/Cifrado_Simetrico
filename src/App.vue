<template>
  <div class="container">
    <label>Texto a cifrar:</label>
    <input v-model="txtOriginal" />

    <button @click="cifrar">Cifrar</button>
    <p>Texto cifrado: {{ txtCifrado }}</p>

    <button @click="descifrar">Descifrar</button>
    <p>Texto descifrado: {{ txtDescifrado }}</p>
  </div>
</template>

<script>
import CryptoJS from "crypto-js";

export default {
  data() {
    return {
      txtOriginal: "",
      txtCifrado: "",
      txtDescifrado: "",
      clave: "carlos18",
    };
  },
  methods: {
    cifrar() {
      this.txtCifrado = CryptoJS.DES.encrypt(this.txtOriginal, this.clave).toString();
    },
    descifrar() {
      const bytes = CryptoJS.DES.decrypt(this.txtCifrado, this.clave);
      this.txtDescifrado = bytes.toString(CryptoJS.enc.Utf8);
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  font-family: sans-serif}

label {
  display: block;
  margin-bottom: 10px;
}

input {
  width: 100%;
  padding: 8px;
  margin-bottom: 15px;
}

button {
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
  font-weight: bold;
}
</style>
