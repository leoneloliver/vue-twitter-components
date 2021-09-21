<template>
    <div>
        <div class="px-5 py-3 border-b border-gray-100 flex items-center justify-between">
            <h1 class="text-xl font-bold">Home</h1>
            <i class="fa fa-star text-xl text-blue-400"></i>
          </div>
          <div class="px-5 py-3 border-b-4 border-gray-100 flex">
            <div class="flex-none">
              <img src="profile.jpg" class="flex-none w-12 h-12 rounded-full border border-gray-200"/>
            </div>
            <form v-on:submit.prevent = "addNewTweet" class="w-full px-4 relative">
              <textarea v-model="tweet.content" placeholder="What's up?" class="mt-3 pb-3 w-full focus:outline-none" id="box"/>
              <div class="flex items-center">
                <i class="text-lg text-blue-400 mr-4 fa fa-image"></i>
                <i class="text-lg text-blue-400 mr-4 fa fa-film"></i>
                <i class="text-lg text-blue-400 mr-4 fa fa-bar-chart"></i>
                <i class="text-lg text-blue-400 mr-4 fa fa-smile-o"></i>
              </div>
              <button type="submit" class="h-10 px-4 text-white font-semibold bg-blue-400 hover:bg-blue-500 focus:outline-none rounded-full absolute bottom-1 right-0">
                Tweet
              </button>
            </form>
          </div>
          <div class="flex flex-col-reverse">
            <div v-for="tweet in tweets" :key="tweet.content" class="w-full p-4 border-b hover:bg-gray-100 flex">
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
    }
  }
}
</script>

<style scoped>

</style>
