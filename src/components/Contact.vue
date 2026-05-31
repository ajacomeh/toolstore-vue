<script setup>

import { ref } from "vue"

const name = ref("")
const email = ref("")
const product = ref("")
const quantity = ref("")
const terms = ref(false)

const handleSubmit = () => {

  if(name.value.trim().length < 3){
    alert("Ingrese un nombre válido")
    return
  }

  if(!email.value.includes("@")){
    alert("Ingrese un correo válido")
    return
  }

  if(product.value === ""){
    alert("Seleccione un producto")
    return
  }

  if(quantity.value <= 0){
    alert("Ingrese una cantidad válida")
    return
  }

  if(!terms.value){
    alert("Debe aceptar los términos y condiciones")
    return
  }

  alert("Pedido enviado correctamente")
}

</script>

<template>

  <section
    id="contact"
    class="contact"
  >

    <h2>
      Realizar Pedido
    </h2>

    <form
      @submit.prevent="handleSubmit"
    >

      <input
        type="text"
        placeholder="Nombre"
        v-model="name"
      >

      <input
        type="email"
        placeholder="Correo"
        v-model="email"
      >

      <select v-model="product">

        <option value="">
          Seleccione un producto
        </option>

        <option>
          Taladro Inalámbrico
        </option>

        <option>
          Martillo Profesional
        </option>

        <option>
          Sierra Circular
        </option>

        <option>
          Juego de Destornilladores
        </option>

      </select>

      <input
        type="number"
        placeholder="Cantidad"
        v-model="quantity"
      >

      <label>

        <input
          type="checkbox"
          v-model="terms"
        >

        Acepto términos y condiciones

      </label>

      <button type="submit">
        Enviar Pedido
      </button>

    </form>

  </section>

</template>