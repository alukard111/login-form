<template>
  <button 
  
  :class="[...classes]"
  >
    {{ btnName }}
  </button>
</template>

<script>


let classes = [
  'px-7',
  'py-2',
  'mt-4',
  'bg-white',
  'focus:outline-none',
  'ring-4',
  'hover:bg-blue-400',
  'hover:text-white',
  'active:bg-blue-900',
  
  'rounded-full',
  
]

export default {
  props: {
    btnName: {
      type: [String, Number],
      default: () => ''
    },
  },

  computed: {
    classes() {
      return classes
    },
  },

 
}
</script>