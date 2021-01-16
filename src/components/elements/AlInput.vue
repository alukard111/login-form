<template>
  <div 
  :class="[...mainDivBox]"
  >
    <label
      v-text="`${label}`"
      class="m-2"
    /> 
      
    <input
      :class="[...classesInput]"
      :placeholder="placeholder"
      :type="type"
    />
    
  </div>
</template>

<script>
let mainDivBox = [
  'block',  
  'px-7',
  'py-4',
  'hover:shadow-lg',
  'rounded-lg',
  'hover:bg-blue-300',
]

let classesInput = [
  'px-10',
  'py-5',
  'm-3',
  'rounded-lg',
  'self-center',
  'focus:bg-white',
  'border',
]

  export default {
    props: {
      
      
      placeholder: {
        type: [String, Number],
        default: () => 'Placeholder'
      },
      
      label : {
        type: [String, Number],
        default: () => 'Label'
      },

      type: {
        type: String,
        default: () => 'text'
      },

      errorMail: {
        type: String,
        default: () => ''

      },

      errorPass: {
        type: String,
        default: () => ''
      },

      reBorder: {
        type: String,
        default: () => null
      }


    },

    

    computed: {
      classesInput() {
        let res = classesInput
        let red = 'border-red-400'
        let green = 'border-green-400'
        
        

        if (this.errorMail === 'warning') {
          res.push(red)
          this.removeItemAll(green)
        } 

        if (this.errorPass === 'warning') {
          res.push(red)
          this.removeItemAll(green)
        } 

        if (this.errorMail === 'success') {
          res.push(green)
          this.removeItemAll(red)
          
        }

        if (this.errorPass === 'success') {
          res.push(green)
          this.removeItemAll(red)
        }

        if (this.reBorder) {
          this.removeItemAll(red)
          this.removeItemAll(green)
        }
        
        return classesInput
      },

      mainDivBox() {
        return mainDivBox
      }
    },

    methods: {
      removeItemAll(value) {
        let i = 0
        while (i < classesInput.length) {
          if (classesInput[i] === value) {
            classesInput.splice(i, 1)
          } else {
            ++i
          }
        }
        return classesInput
      }
    }
    
  
  }
</script>
