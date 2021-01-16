<template>
  <div>
    <div>
      <div>
        <img :src="cat[0]" alt="">
      </div>
      <div
      >
        <AlBtn 
        v-on:click.native="clear"
        :btnName="nameBtn"
        />
        
      </div>
    </div>
  </div>
</template>

<script>
import AlBtn from '@/components/elements/AlBtn.vue'

export default {
  components: {
    AlBtn,
  },

  data: () => {
    return {
      cat: ["https://i.gifer.com/2uG5.gif"],
      nameBtn: 'Выйти из аккаунта',
      
    }
  },

  methods: {
    clear() {
      localStorage.removeItem('login')
      localStorage.removeItem('password')
      location.reload()
    }
  }
}

</script>