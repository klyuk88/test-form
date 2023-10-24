<script setup lang="ts">
import FormInput from "@/components/ui/Form/FormInput.vue"
import TheButton from "@/components/ui/Buttons/TheButton.vue"
import { useForm } from "vee-validate"
import * as yup from "yup"
import FormTextArea from "@/components/ui/Form/FormTextArea.vue"
import { computed } from "vue"

const ValidateFormMessages = {
  requiredMsg: "Обязательное поле",
  phoneMsg: "Телефон должен состоять из 10 цифр"
}

const { values, errors, handleReset } = useForm({
  validationSchema: yup.object({
    name: yup.string().required(ValidateFormMessages.requiredMsg).max(100),
    lastName: yup.string().max(100),
    email: yup.string().required(ValidateFormMessages.requiredMsg).email(),
    phone: yup
      .string()
      .required(ValidateFormMessages.requiredMsg)
      .min(18, ValidateFormMessages.phoneMsg),
    text: yup.string().max(500)
  })
})
const onSubmit = () => {
  console.log(values)
  setTimeout(() => {
    handleReset()
  }, 1000)
}
const isErrorValidation = computed(() => {
  return Object.keys(errors.value).length > 0
})

const isValuesNotEmpty = computed(() => {
  return !!(values.name && values.lastName && values.email && values.phone && values.text)
})
</script>
<template>
  <form :class="$style.form" novalidate @submit.prevent="onSubmit">
    <FormInput placeholder="Введите имя" name="name" />
    <FormInput placeholder="Введите фамилию" name="lastName" />
    <FormInput
      placeholder="Введите телефон"
      :type="'tel'"
      name="phone"
      :mask="'+7 (###) ###-##-##'"
    />
    <FormInput placeholder="Введите e-mail" :type="'email'" name="email" />
    <FormTextArea placeholder="Введите ваше сообщение" name="text" />
    <TheButton title="Отправить" :disabled="isErrorValidation || !isValuesNotEmpty" />
  </form>
</template>
<style module lang="scss">
.form {
  display: flex;
  flex-direction: column;
  gap: 15px;
  width: 500px;
}
</style>
