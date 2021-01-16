<template>
  <div
  :class="[...divMainBox]">
    
    <div 
    :class="[...divContentBox]">
      
      <form action="#"
      @submit.prevent="checkForm"
      :class="[...classForm]"> 
        <AlInput 
        v-model="statusMail"
        placeholder="Input email"
        label="Email" 
        type="email"
        :errorMail="errorMail"
        />
        
        
        <AlInput
        v-model="statusPass"
        placeholder="Input pass"
        label="Password"
        type="password"
        :errorPass="errorPass"
        />
        
        <AlBtn 
        :btnName="nameBtn"
        type="submit"
        />
        
        
      </form>
      <div v-if="loading">
        <AlLoader />
      </div>
      
    </div>
  </div>
</template>

<script>
import AlInput from '@/components/elements/AlInput.vue'
import AlBtn from '@/components/elements/AlBtn.vue'
import AlLoader from '@/components/AlLoader.vue'


let classForm = ['']
let divMainBox = [
  'flex',
  'justify-center'
]

let divContentBox = [
  'rounded-lg',
  'container',
  'p-12',
  'm-12',  
  'w-96',
  'h-100',
  'text-center',
  'shadow-2xl', 
  'flex',
  'justify-center'
]

export default {
  components: {
    AlInput,
    AlBtn,
    AlLoader,
  },

  data: () => {
    return {
      errorMail: '',
      errorPass: '',
      statusMail: '',
      statusPass: '',
      loading: false,
      nameBtn: 'Войти'
    }
    
  },

  mounted() {
    if (localStorage.login && localStorage.password) {
      this.loading = true
    } 
  },

  computed: {
    classForm() {     
      if (this.loading) {
        classForm.push('hidden')
      }
      return classForm
    },

    divMainBox() {
      return divMainBox
    },

    divContentBox() {
      return divContentBox
    }



    
    
  },

  methods: {
    validateEmail(email) {
      const re = /^(([^<>()\[\]\.,;:\s@\"]+(\.[^<>()\[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i
      return re.test(email)
    },

    checkForm(e) {
      this.errorMail = ''
      this.errorPass = ''
      this.statusMail = ''
      this.statusPass = ''
      


      this.statusMail = e.target[0].value
      this.statusPass = e.target[1].value

      let validMail = this.validateEmail(this.statusMail)
      if (validMail) {
        console.log('mail accept')
      } else {
        console.log('no valid')
      }

      if (validMail && this.statusPass) {
        this.loading = true
        this.errorMail = 'success'
        this.errorPass = 'success'
        this.localstorage(this.statusMail, this.statusPass)
        return true
      } else {
        this.loading = false
      }

      if (validMail) {
        this.errorMail = 'success'
      } else {
        this.errorMail = 'warning'
      }

      if (this.statusPass) {
        this.errorPass = 'success'
      } else {
        this.errorPass = 'warning'
      }
    },

    localstorage(mail, pass) {
      localStorage.setItem('login', mail)
      localStorage.setItem('password', pass)
      
    }
  },
}


</script>
