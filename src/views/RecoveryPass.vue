<template>
  <div :class="divMainBox">
    <form 
    action="#"
    @submit.prevent="checkValidate">
      <h1 v-if="mail">Письмо ушло на почту</h1>
      <AlInput
      
      placeholder="Input email"
      label="Email"
      type="email"
      class="border-transparent"
      :reBorder="reBorder"
      />
      <AlBtn
      type="submit"
      :btnName="nameBtn" />

    </form>
  </div>
</template>

<script>
import AlInput from '@/components/elements/AlInput.vue'
import AlBtn from '@/components/elements/AlBtn.vue'

let divMainBox = [
  'text-center',
  'pt-4',
  'flex',
  'justify-center']

export default {
  components: {
    AlInput,
    AlBtn
  },

  data: () => {
    return {
      mail: '',
      reBorder: 'clear',
      nameBtn: 'Восстановить пароль'
    }
  },

  computed: {
    divMainBox() {
      return divMainBox
    }
  },

  methods: {
    validateEmail(email) {
      const re = /^(([^<>()\[\]\.,;:\s@\"]+(\.[^<>()\[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i
      return re.test(email)
    },
    
    
    checkValidate(e) {
      console.log(e.target[0].value)
      this.mail = e.target[0].value

      let validMail = this.validateEmail(this.mail)
      if (validMail) {
        alert('Пароль отправлен на вашу почту')
      } else {
        alert('Поле email заполнено не верно')
      }
    }
  }
}

</script>