<script setup>

import { ref } from "vue"

const name = ref("")
const email = ref("")
const product = ref("")
const quantity = ref("")
const terms = ref(false)

const nameError = ref("")
const emailError = ref("")
const productError = ref("")
const quantityError = ref("")
const termsError = ref("")

const validateName = (value) => {

  name.value = value

  if(value.trim().length < 3){
    nameError.value =
      "El nombre debe tener al menos 3 caracteres."
  }else{
    nameError.value = ""
  }

}

const validateEmail = (value) => {

  email.value = value

  const regex =
    /^[^\s@]+@[^\s@]+\.[^\s@]+$/

  if(!regex.test(value)){
    emailError.value =
      "Ingrese un correo válido."
  }else{
    emailError.value = ""
  }

}

const validateProduct = (value) => {

  product.value = value

  if(value === ""){
    productError.value =
      "Seleccione un producto."
  }else{
    productError.value = ""
  }

}

const validateQuantity = (value) => {

  quantity.value = value

  if(value <= 0 || value === ""){
    quantityError.value =
      "La cantidad debe ser mayor a 0."
  }else{
    quantityError.value = ""
  }

}

const validateTerms = (checked) => {

  terms.value = checked

  if(!checked){
    termsError.value =
      "Debe aceptar los términos y condiciones."
  }else{
    termsError.value = ""
  }

}

const handleSubmit = () => {

  if(
    nameError.value ||
    emailError.value ||
    productError.value ||
    quantityError.value ||
    termsError.value ||
    !name.value ||
    !email.value ||
    !product.value ||
    !quantity.value ||
    !terms.value
  ){

    alert(
      "Por favor corrija los errores antes de enviar."
    )

    return
  }

  alert("Pedido enviado correctamente.")

  name.value = ""
  email.value = ""
  product.value = ""
  quantity.value = ""
  terms.value = false

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
        placeholder="Nombre completo"
        :value="name"
        @input="validateName($event.target.value)"
        :class="nameError ? 'input-error' : ''"
      >

      <span
        v-if="nameError"
        class="error"
      >
        {{ nameError }}
      </span>

      <input
        type="email"
        placeholder="Correo electrónico"
        :value="email"
        @input="validateEmail($event.target.value)"
        :class="emailError ? 'input-error' : ''"
      >

      <span
        v-if="emailError"
        class="error"
      >
        {{ emailError }}
      </span>

      <select
        :value="product"
        @change="validateProduct($event.target.value)"
        :class="productError ? 'input-error' : ''"
      >

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

      <span
        v-if="productError"
        class="error"
      >
        {{ productError }}
      </span>

      <input
        type="number"
        placeholder="Cantidad"
        :value="quantity"
        @input="validateQuantity($event.target.value)"
        :class="quantityError ? 'input-error' : ''"
      >

      <span
        v-if="quantityError"
        class="error"
      >
        {{ quantityError }}
      </span>

      <label class="terms-label">

        <input
          type="checkbox"
          :checked="terms"
          @change="validateTerms($event.target.checked)"
        >

        Acepto los términos y condiciones

      </label>

      <span
        v-if="termsError"
        class="error"
      >
        {{ termsError }}
      </span>

      <button type="submit">
        Enviar Pedido
      </button>

    </form>

  </section>

</template>