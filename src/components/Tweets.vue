<template>
    <div>
      <div class="px-5 py-3 border-b border-gray-100 dark:border-gray-800 flex items-center justify-between">
        <h1 class="text-xl font-bold dark:text-gray-300">Home</h1>
        <!-- <i class="fa fa-star text-xl text-blue-400"></i> -->
        <div>
          <button @click="this.darkMode">
            <span v-if="darkTheme" class="sun"><i class="fa fa-sun-o text-yellow-200 text-lg" aria-hidden="true"></i></span>
            <span v-else class="moon"><i class="fa fa-moon-o text-gray-100 text-lg" aria-hidden="true"></i></span>
          </button>
        </div>
      </div>
      <div class="px-5 py-3 border-b-4 border-gray-100 dark:border-gray-800 flex">
        <div class="flex-none">
          <img src="profile.jpg" class="flex-none w-12 h-12 rounded-full border border-gray-200 dark:border-gray-800"/>
        </div>
        <form v-on:submit.prevent = "addNewTweet" class="w-full px-4 relative">
          <textarea v-model="tweet.content" placeholder="What's up?" class="mt-3 pb-3 w-full focus:outline-none dark:bg-black dark:text-gray-300" id="box"/>
          <div class="flex items-center">
            <i class="text-lg text-blue-400 dark:text-blue-500 mr-4 fa fa-image"></i>
            <i class="text-lg text-blue-400 dark:text-blue-500 mr-4 fa fa-film"></i>
            <i class="text-lg text-blue-400 dark:text-blue-500 mr-4 fa fa-bar-chart"></i>
            <i class="text-lg text-blue-400 dark:text-blue-500 mr-4 fa fa-smile-o"></i>
          </div>
          <button type="submit" class="h-10 px-4 text-white font-semibold bg-blue-400 hover:bg-blue-500 focus:outline-none rounded-full absolute bottom-1 right-0">
            Tweet
          </button>
        </form>
      </div>
      <div class="flex flex-col-reverse">
        <div v-for="tweet in tweets" :key="tweet.content" class="w-full p-4 border-b dark:border-gray-800 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-black flex">
          <div class="flex-none mr-4">
            <img :src="`${tweet.src}`" class="h-12 w-12 rounded-full flex-none"/>
          </div>
          <div class="w-full">
            <div class="flex items-center w-full">
              <p class="font-semibold">{{tweet.name}} </p>
              <p class="text-sm text-dark ml-2">{{tweet.handle}} </p>
              <p class="text-sm text-dark ml-2 md:block hidden "> 1 sec </p>
              <i class="fa fa-ellipsis-h text-sm text-gray-500 ml-auto md:block hidden "></i>
              
            </div>
            <p class="py-2" v-html="tweet.content" >
              <!-- {{ tweet.content }} -->
            </p>
            <div class="flex items-center justify-between w-full">
              <div class="flex items-center text-sm text-dark">
                <i class="fa fa-comment-o mr-3 text-gray-500"></i>
                <p> 0 </p>
              </div>
              <div class="flex items-center text-sm text-dark">
                <i class="fa fa-retweet mr-3 text-gray-500"></i>
                <p> 0 </p>
              </div>
              <div class="flex items-center text-sm text-dark">
                <i class="fa fa-heart-o mr-3 text-gray-500"></i>
                <p> 1 </p>
              </div>
              <div class="flex items-center text-sm text-dark">
                <i class="fa fa-share mr-3 text-gray-500"></i>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'SideBar',
  props: {
    darkTheme: Boolean,
  },
  data() {
    return {
      tweets: [
        {content: 'Cool tell me more!', src: 'luis.jpg', name: 'Luis Stocvis', handle: '@lrogers'},
        {content: 'Have you guys tried it?<br/><img src="vue.jpg" class="mt-3 mb-3 rounded-lg" />', src: 'harry.jpg', name: 'Harrry Musk', handle: '@teslaBoy'}
      ],
      tweet: {content: ''}
    }
  },
  methods: {
    addNewTweet () {
      let newTweet = {
        content: this.tweet.content,
        src: 'profile.jpg', 
        name: 'Riana Maia', 
        handle: '@RiMaiaz01'
      };
      this.tweets.push(newTweet)
      // this.tweets.push({content: this.tweet.content})
      this.tweet.content = ''
    },
    darkMode () {
      document.querySelector('html').classList.toggle('dark');
      this.darkTheme = !this.darkTheme;
    }
  }
}
</script>

<style scoped>
.moon{
  background: #9da4b0;
  border-radius: 500px;
  padding: 3px 7px;
}
.sun{
  background: #333;
  border-radius: 500px;
  padding: 3px 6px;
}

</style>
