<template>
  <div>
    <div class="al-scroll-box" 
    >
      <div 
        class="al-content-scroll" 
        @scroll="moreContent()"
      >
        <div 
          
          class="flex justify-center"
          v-for="cat in cats"
          :key="cat.id"
          
        >
          <img 
            class="this-img"
            :src="cat"
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      InfiniteScroll: 'Infinite Scroll here',
      cats: [
        'https://wallbox.ru/wallpapers/preview/201647/14797178325832b3c89f9898.95980224.jpg',
        'https://64.media.tumblr.com/tumblr_lgr4pclZmR1qdvbl3o1_500.jpg',
        'https://cs9.pikabu.ru/post_img/big/2017/04/20/0/1492637184115362138.jpg',
      ],

      partyCat:'https://phoneky.co.uk/thumbs/screensavers/down/fun/funnycat_1hN1Hulr.gif'
    
    }),
   

        
    
    
    methods: {

      // more content to god of content
      moreContent() {
        let contentScroll = document.querySelector('.al-content-scroll')
        let windowRelativeBottom = document.documentElement.getBoundingClientRect().bottom
        if (windowRelativeBottom < document.documentElement.clientWidth + 40) {
          
          contentScroll.insertAdjacentHTML('beforeend', `<img src=${this.partyCat} style="margin:40px 120px;" >`)
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  @layer base {
    .al-scroll-box {
      @apply 
        flex
        h-96
        justify-center;
    }
    .al-content-scroll {
      @apply
        grid
        grid-cols-3
        overflow-scroll
        border-2
        w-8/12
        bg-blue-400
        text-white;
    }
    .btn-scroll {
      @apply 
        active:bg-yellow-100
        outline-none;
    }

    .this-img {
      @apply
        m-8
        w-auto
        h-80

    }
  }

</style>