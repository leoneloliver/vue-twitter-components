<template>
    <div class="mt-3">
          
        <h1 class="text-xl font-bold px-5 py-3 border-b border-gray-100 dark:border-gray-800 flex items-center justify-between dark:text-gray-300">Who to follow</h1>
         
          <div v-for="follow in following" :key="follow.tweet" class="w-full dark:text-gray-200 p-4 border-b dark:border-gray-800 hover:bg-gray-100 dark:hover:bg-black flex">
            
            <div class="flex-none mr-4">
              <img :src="`${follow.src}`" class="h-12 w-12 rounded-full flex-none"/>
            </div>
            <div class="w-full">
              <div class="flex items-center w-full">
                <p class="font-semibold"> {{ follow.name }} </p>
                <p class="text-sm text-dark ml-2"> {{ follow.handle }} </p>
                <p class="text-sm text-dark ml-2 md:block hidden "> {{ follow.time }} </p>
                <i class="fa fa-angle-down text-dark ml-auto md:block hidden "></i>
              </div>
              <p class="py-2">
                {{ follow.tweet }}
              </p>
              <div class="flex items-center justify-between w-full">
                <div class="flex items-center text-sm text-dark">
                  <i class="fa fa-comment-o mr-3 text-gray-500"></i>
                  <p> {{ follow.comments }} </p>
                </div>
                <div class="flex items-center text-sm text-dark">
                  <i class="fa fa-retweet mr-3 text-gray-500"></i>
                  <p> {{ follow.retweets }} </p>
                </div>
                <div class="flex items-center text-sm text-dark md:flex hidden ">
                  <i class="fa fa-heart-o mr-3 text-gray-500"></i>
                  <p> {{ follow.like }} </p>
                </div>
                <div class="flex items-center text-sm text-dark">
                  <i class="fa fa-share mr-3 text-gray-500"></i>
                </div>
              </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'SideBar',
  data() {
    return {
      following: [
        {src: 'gina.jpg', name: 'Gina Kim', handle: '@gKimhong', time: '55 min', tweet: 'Should me and the rock do another sub-par movie together????', comments: '2,030', retweets: '50', like: '20,003'},
        {src: 'kevin.jpg', name: 'Kevin Doh', handle: '@kevindoh', time: '20 min', tweet: 'Should I just quarantine on mars??', comments: '1,000', retweets: '550', like: '1,225'},
        {src: 'tina.jpg', name: 'Tina Tompson', handle: '@topson03', time: '1.4 hr', tweet: 'Haha just made a flame thrower. Shld I sell them?', comments: '100,000', retweets: '1,109', like: '5,093'},
      ]
    }
  }
}
</script>

<style scoped>

</style>
