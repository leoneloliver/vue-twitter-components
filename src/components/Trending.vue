<template>
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
            <div class="hidden lg:block ml-4 text-left">
              <p class="text-sm font-bold leading-tight"> {{ friend.name }} </p>
              <p class="text-xs"> {{ friend.handle }} </p>
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
</template>

<script>
export default {
  name: 'SideBar',
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
      ]
    }
  }
}
</script>

<style scoped>
.ico-search{
  margin-top: 16px;
}
</style>
