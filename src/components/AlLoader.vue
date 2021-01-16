<template>
  <div
  id="about"
  >
   
    <div
    :class="[...classDiv]"
    >
      <h1>
        Загружено: {{ progress }}%
      </h1>
      <div 
      :class="[...mainBoxDiv]"
      >
        <div
        :class="[...firstMainChildBox]"
        >
        </div>
        <div
        id="bar"
        :class="[...lastMainChildBox]"
        >
        
        </div>
      </div>
     
    </div>
    <div v-if="progress >= 100">
      <AlContent 
      />
    </div>
  </div>
</template>

<script>
import AlContent from '@/components/AlContent.vue'

let classDiv = ['']
let mainBoxDiv = [
  'h-6',
  'relative',
  'max-w-xs',
  'rounded-lg',
  'overflow-hidden'
]

let firstMainChildBox = [
  'w-full',
  'h-full',
  'bg-gray-300',
  'absolute',
]

let lastMainChildBox = [
  'h-full',
  'bg-green-500',
  'relative',
  'w-12',
]

export default {
  components: {
    AlContent
  },

  data: () => {
    return {
      progress: 0,
      invervalSpeed: 10,
      incrementSpeed: 1,
      
    }
  },

  

  mounted() {
    this.progressInterval()
    

  },

  computed: {
    classDiv() {
      let classes = classDiv
      
      if (this.progress === 100) {
        classes.push('hidden')
      }
      return classDiv
    },

    mainBoxDiv() {
      return mainBoxDiv
    },

    firstMainChildBox() {
      return firstMainChildBox
    },

    lastMainChildBox() {
      return lastMainChildBox
    }
  },



  methods: {
    progressInterval() {
        let bar = document.getElementById('bar')
        let progressInt = setInterval(() => {
          this.progress += this.incrementSpeed
          bar.style.width = this.progress + "%"
          if (this.progress >= 100) {
            clearInterval(progressInt)
          }
      }, this.incrementSpeed)
      
    }
  }

   
  
}


</script>