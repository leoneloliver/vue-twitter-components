<template>
    <div class="w-1/4 border-r border-gray-100 px-2 md:px-8 py-2 flex flex-col justify-between">
        <div>
          <button class="ml-2 h-12 w-12 hover:bg-blue-100 text-3xl rounded-full text-blue-400">
            <i class="fa fa-twitter" id="ttt"></i>
          </button>
          <div>
              <button v-for="tab in tabs" @click="id=tab.id" :key="tab.id" :class="`focus:outline-none hover:text-blue-400 flex items-center py-2 px-4 hover:bg-gray-100 rounded-full mr-auto mb-3 ${id === tab.id ? 'text-blue-400' : null}`">
              <i :class="`${ tab.icon } text-2xl mr-4 text-left`"></i>
              <p class="text-lg font-semibold text-left hidden lg:block"> {{ tab.title }} </p>
            </button>
          </div>
          <button class="text-white bg-blue-400 rounded-full font-semibold focus:outline-none w-full p-3 hover:bg-blue-500">
            Tweet
          </button>
        </div>

        <div class="w-full">
          
          <div class="relative">
            <div v-if="dropdown === true" class="absolute popup -mt-10 bottom-0 left-0 w-64 rounded-lg shadow-md border-gray-100 bg-white mb-4">
              <button @click="dropdown = false" class="p-3 flex items-center w-full hover:bg-gray-100  p-2 focus:outline-none">
                <img src="profile.jpg" class="w-10 h-10 rounded-full border border-gray-200" />
                <div class="ml-4">
                  <p class="text-sm font-bold leading-tight">Riana Maia</p>
                  <p class="text-sm leading-tight">@RiMaiaz01 </p>
                </div>
                <i class="fa fa-check ml-auto text-blue-400"></i>
              </button>
              <button @click="dropdown = false" class="w-full text-left hover:bg-gray-100  border-t border-gray-100 p-3 test-sm focus:outline-none">
                Add an existing account
              </button>
              <button @click="dropdown = false" class="w-full text-left hover:bg-gray-100  border-t border-gray-100 p-3 test-sm focus:outline-none">
                Log out @RiMaiaz01
              </button>
            </div>
          </div>

          <button @click="dropdown = true" class="flex items-center w-full hover:bg-gray-100 rounded-full p-2 focus:outline-none">
            <img src="profile.jpg" class="w-10 h-10 rounded-full border border-gray-200" />
            <div class="ml-4 hidden md:block">
              <p class="text-sm font-bold leading-tight pl-0">Riana Maia</p>
              <p class="text-sm leading-tight pl-0">@RiMaiaz01</p>
            </div>
            <i class="fa fa-ellipsis-h text-sm ml-auto mr-2"></i>
          </button>

        </div>

    </div>
    
</template>

<script>
export default {
  name: 'SideBar',
  data() {
    return {
      tabs: [
        {icon: 'fa fa-home', title: 'Home', id:'home'},
        {icon: 'fa fa-hashtag', title: 'Explore', id: 'explore'},
        {icon: 'fa fa-bell', title: 'Notifications', id: 'notifications'},
        {icon: 'fa fa-envelope', title: 'Messages', id: 'messages'},
        {icon: 'fa fa-bookmark', title: 'Bookmarks', id: 'bookmarks'},
        {icon: 'fa fa-clipboard', title: 'Lists', id: 'lists'},
        {icon: 'fa fa-user', title: 'Profile', id: 'profile'},
        {icon: 'fa fa-ellipsis-h', title: 'More', id: 'more'}
      ],
      id: 'home',
      dropdown: false,
      
    }
  }
}
</script>

<style scoped>

</style>
