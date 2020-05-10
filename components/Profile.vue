<template>
  <div class="flex items-center divide-x divide-gray-300">
    <div class="flex items-center pr-6">
      <img src="../assets/images/coin-icon.svg" width="26" height="26" alt="" />
      <span class="ml-2 mr-4 text-xl font-medium">323</span>
      <button
        class="text-xs font-light border border-red-400 hover:border-red-600 text-red-400 hover:text-red-600 rounded-md bg-white transition-shadow duration-200 ease-in-out hover:shadow-md py-2 px-3 "
      >
        Redeem
      </button>
    </div>
    <div class="flex items-center pl-5 text-xl leading-3">
      <button>
        <img
          src="../assets/images/notifications-icon.svg"
          width="25"
          height="25"
          alt=""
          class="transition-opacity duration-300 ease-in-out hover:opacity-75"
        />
      </button>
      <div class="ml-4 profile-img-holder">
        <button>
          <img
            src="../assets/images/profiles/profile1.png"
            width="40"
            height="40"
            alt="Profile 1"
            class="rounded-full transition-shadow duration-200 ease-in-out hover:shadow"
          />
        </button>
      </div>
    </div>
  </div>
</template>
