<template>
    <div class="flex container h-screen w-full">
  
      <!-- side bar -->
      <Sidebar />
      <!-- end sidebr -->

      <!-- main page -->
      <div class="w-full md:w-1/2 h-full overflow-y-auto">
        <!-- tweets -->
        <Tweets />
        <!-- end tweets -->

        <!-- followers -->
        <Followers />
        <!-- follwers -->  
      </div>
      <!-- end main page -->

      <!-- trending -->
      <Trending />
      <!-- end trending -->

    </div>
</template>

<script>

import Sidebar from './SideBar.vue'
import Tweets from './Tweets.vue'
import Followers from './Followers.vue'
import Trending from './Trending.vue'

export default {
  name: 'Home',
  props: {
    title: String
  },
  components: {
    Sidebar,
    Tweets,
    Followers,
    Trending
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

body{
  margin: 0;
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
