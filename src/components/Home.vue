<template>
    <div class="flex container h-screen w-full">
  
      <!-- side bar -->
      <Sidebar />
      <!-- end sidebr -->


      <!-- main page -->
      <div class="w-full md:w-1/2 h-full overflow-y-auto">


        <!-- tweets -->
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
                    <i class="fa fa-comment mr-3"></i>
                    <p> 0 </p>
                  </div>
                  <div class="flex items-center text-sm text-dark">
                    <i class="fa fa-retweet mr-3"></i>
                    <p> 0 </p>
                  </div>
                  <div class="flex items-center text-sm text-dark">
                    <i class="fa fa-heart mr-3"></i>
                    <p> 1 </p>
                  </div>
                  <div class="flex items-center text-sm text-dark">
                    <i class="fa fa-share-square mr-3"></i>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- end tweets -->

        <!-- followers -->
        <div class="mt-3">
          
          <h1 class="text-xl font-bold px-5 py-3 border-b border-gray-100 flex items-center justify-between">Who to follow</h1>
         
          <div v-for="follow in following" :key="follow.tweet" class="w-full p-4 border-b hover:bg-gray-100 flex">
            
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
                  <i class="fa fa-comment mr-3"></i>
                  <p> {{ follow.comments }} </p>
                </div>
                <div class="flex items-center text-sm text-dark">
                  <i class="fa fa-retweet mr-3"></i>
                  <p> {{ follow.retweets }} </p>
                </div>
                <div class="flex items-center text-sm text-dark md:block hidden ">
                  <i class="fa fa-heart mr-3"></i>
                  <p> {{ follow.like }} </p>
                </div>
                <div class="flex items-center text-sm text-dark">
                  <i class="fa fa-share-square mr-3"></i>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- follwers -->

      
      </div>
      <!-- end main page -->


      <!-- trending -->
      <div class="md:block hidden w-1/3 h-full border-l border-lighter py-2 px-6 overflow-y-scroll relative">
        <input class="pl-12 rounded-full w-full p-2 bg-gray-200 text-sm mb-4 focus:outline-none " placeholder="Search Twitter" />
        <i class="fa fa-search absolute left-0 top-0 mt-1 mt-5 ml-12 text-sm text-gray-400 ico-search" ></i>
        <div class="w-full rounded-lg bg-gray-100">
          <div class="flex items-center justify-between p-3">
            <p class="text-lg font-bold">Trends for You</p>
            <i class="fa fa-cog text-lg text-blue-400"></i>
          </div>
          <button v-for="trend in trending" :key="trend.title" class="w-full flex justify-between hover:bg-gray-200 p-3 border-t border-gray-200">
            <div>
              <p class="text-xs text-left leading-tight"> {{ trend.top}} </p>
              <p class="font-bold text-sm text-left leading-tight text-black"> {{ trend.title}} </p>
              <p class="text-left text-xs leading-tight text-dark"> {{ trend.bottom}} </p>
            </div>
            <i class="fa fa-ellipsis-h text-gray-600"></i>
          </button>
          <button class="p-3 w-full hover:bg-gray-200 text-left text-blue-400 border-t border-gray-200">
            Show More
          </button>
        </div>
        <div class="w-full rounded-lg bg-gray-100 my-4">
          <div class=" p-3">
            <p class="text-lg font-bold">Who to Follow</p>
          </div>
          <button v-for="friend in friends" :key="friend.name" class="w-full flex hover:bg-gray-200 p-3 border-t border-gray-200">
            <img :src="`${ friend.src }`" class="w-12 h-12 rounded-full border border-gray-100" />
            <div class="hidden lg:block ml-4">
              <p class="text-sm font-bold leading-tight"> {{ friend.name }} </p>
              <p class="text-xs -ml-2"> {{ friend.handle }} </p>
            </div>
            <button class="bg-gray-700 hover:bg-gray-900 ml-auto text-white text-sm  py-1 px-4 rounded-full border-2 border-black-400">
              Follow
            </button>
          </button>
          <button class="p-3 w-full hover:bg-gray-200 text-left text-blue-400 border-t border-gray-200">
            Show More
          </button>
        </div>
      </div>
      <!-- end trending -->

    </div>
     


</template>

<script>

import Sidebar from './SideBar.vue'

export default {
  name: 'Home',
  props: {
    title: String
  },
  components: {
    Sidebar
  },
  data() {
    return {
      trending: [
        {top: 'Music', title: 'We Won', bottom: '135K Tweets'},
        {top: 'Pop', title: 'Blue Ivy', bottom: '40k tweets'},
        {top: 'Trending in US', title: 'Denim Day', bottom: '40k tweets'},
        {top: 'Trending', title: 'When Beyonce', bottom: '25.4k tweets'},
      ],
      friends: [
        {src: 'gina.jpg', name: 'Gina Kim', handle: '@gKimhong'},
        {src: 'tina.jpg', name: 'Tina Tompson', handle: '@topson03:)'},
        {src: 'kevin.jpg', name: 'Kevin Hart', handle: '@miniRock'}
      ],
      following: [
        {src: 'gina.jpg', name: 'Gina Kim', handle: '@gKimhong', time: '55 min', tweet: 'Should me and the rock do another sub-par movie together????', comments: '2,030', retweets: '50', like: '20,003'},
        {src: 'kevin.jpg', name: 'Kevin Doh', handle: '@kevindoh', time: '20 min', tweet: 'Should I just quarantine on mars??', comments: '1,000', retweets: '550', like: '1,000,003'},
        {src: 'tina.jpg', name: 'Tina Tompson', handle: '@topson03', time: '1.4 hr', tweet: 'Haha just made a flame thrower. Shld I sell them?', comments: '100,000', retweets: '1,000,002', like: '5,000,003'},
      ],
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

body{
  margin: 0;
}
.ico-search{
  margin-top: 16px;
}
.popup{
  box-sizing: border-box;
}
/* width */
::-webkit-scrollbar {
  width: 1px;
}

/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 0 #f3f4f6;
  border-radius: 0px;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #f3f4f6;
  border-radius: 0px;
}


</style>
