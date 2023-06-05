<template>
  <div class="h-screen   bg-white-100" id="side-bar" :class="dataOpenSideBar == true ? 'side-bar-visible' : 'side-bar-close'">
    <div class="bg-blue-400 h-[50px] flex justify-center items-center ">
      <div class="text-xl font-bold text-center flex items-center justify-center text-black h-full" v-show="dataOpenSideBar">SD Negri 02</div>
      <img src="https://pngimg.com/uploads/minions/minions_PNG42.png" v-show="!dataOpenSideBar" class="p-1 w-8 h-8 rounded-full ring-2 ring-black-100 dark:ring-black-100 " alt="Avatar" />
    </div>
    <div class="flex flex-col justify-between h-[calc(100vh-3rem)] bg-grey-50">
      <div class="menu-man text-left px-6 whitespace-nowrap ">
        <div class="profile flex justify-center items-center text-center py-10 px-8 ">
          <div class="text-center  text-white" v-show="dataOpenSideBar">
            <img src="https://pngimg.com/uploads/minions/minions_PNG42.png" class="p-1 w-24 h-24 rounded-full ring-2 ring-black dark:ring-black mb-4" alt="Avatar" />
            <h5 class="text-xl font-bold leading-tight mb-1 text-black"> Anna Maulina </h5>
            <p class="text-black">Admin </p>
          </div>
        </div>
        <div class="   py-3 rounded-sm cursor-pointer text-black-300 hover:text-blue">
          <router-link to="/dashboard" class="px-2 flex space-x-2"><span class="pi pi-chart-bar" v-tooltip.right="'Dashboard'"></span> <span v-show="dataOpenSideBar">Dashboard</span></router-link>
        </div>
        <div class="   py-3 rounded-md cursor-pointer  text-black-300 hover:text-blue">
          <router-link to="/user" class="px-2 flex space-x-2"><span class="pi pi-user " v-tooltip.right="'User'"></span> <span v-show="dataOpenSideBar">Data Pegawai</span></router-link>
        </div>
        <div class="   py-3 rounded-md cursor-pointer  text-black-300 hover:text-blue">
          <router-link to="/users" class="px-2 flex space-x-2"><span class="pi pi-users" v-tooltip.right="'Product'"></span> <span v-show="dataOpenSideBar">Data Siswa</span></router-link>
        </div>
        <div class="  py-3 rounded-md cursor-pointer text-black-300 hover:text-blue">
          <router-link to="/contact" class="px-2 flex space-x-2"><span class="pi pi-phone" v-tooltip.right="'Contact'"></span> <span v-show="dataOpenSideBar">Contact</span></router-link>
        </div>
        <div class="  py-3 rounded-md cursor-pointer text-black-300 hover:text-blue">
          <div class="px-2 flex space-x-2"><span class="pi pi-cog" v-tooltip.right="'Setting'"></span> <span v-show="dataOpenSideBar">Setting</span></div>
        </div>
      </div>
      <div class="menu-man text-left px-2 justify-self-end whitespace-nowrap">
        <div class="   py-3 rounded-md cursor-pointer text-gray-300 hover:text-gray">
          <a href="https://website-nuxt-front.vercel.app/" target="_blank" class="px-2 flex space-x-2"><span class="pi pi-question" v-tooltip.right="'About Me'"></span> <span v-show="dataOpenSideBar">About Me</span></a>
        </div>
      </div>
    </div>
  </div>
</template>

<script >
export default {
  props: {
    dataOpenSideBar: Boolean
  },

}
</script>

<style>
.p-tooltip-text {
  font-size: 10px !important;
}

#side-bar {
  overflow: hidden;
  transition: 300ms;
}

.side-bar-visible {
  width: 250px !important;
}

.side-bar-close {
  width: 50px !important;
}
</style>