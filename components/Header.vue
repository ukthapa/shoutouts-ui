<template>
  <header
    class="fixed w-full z-40 flex justify-between items-center bg-white border-b border-gray-400 px-4 py-2"
  >
    <div class="flex flex-1 items-center divide-x divide-gray-300">
      <div class="pr-4 flex items-center">
        <div class="pr-3 ">
          <button
            class="transition-opacity duration-300 ease-in-out hover:opacity-50"
          >
            <img
              src="../assets/images/hamburger-icon.svg"
              width="18"
              height="12"
              alt=""
            />
          </button>
        </div>
        <div class="pl-3 text-gray-600 ">
          <nuxt-link
            to="/"
            class="text-opacity-50 flex items-center content-center"
          >
            <img
              src="../static/shoutout-logo.svg"
              width="34"
              height="30"
              alt=""
            />
            <div class="pl-2 font-light text-xl hidden sm:block">Shoutouts</div>
          </nuxt-link>
        </div>
      </div>
      <div class="pl-4 flex-1 self-center leading-10">
        <Search />
      </div>
    </div>
    <div>
      <Profile />
    </div>
  </header>
</template>
<script>
import Search from '~/components/Search'
import Profile from '~/components/Profile'
export default {
  components: {
    Search,
    Profile
  }
}
</script>
