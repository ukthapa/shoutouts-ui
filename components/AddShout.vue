<template>
  <div>
    <div class="grid grid-cols-6  lg:grid-cols-9 gap-4 py-6">
      <div class="col-start-1 col-span-4 lg:col-start-3 lg:col-span-5 relative">
        <div class="card-wrapper">
          <div class="card bg-white rounded-lg p-4 ml-16">
            <div class="card-header clearfix">
              <div class="shoutby">
                <img
                  src="../assets/images/profiles/profile1.png"
                  width="40"
                  height="40"
                  alt="Profile 1"
                  class="h-12 w-12 rounded-full border-2 border-white"
                />
              </div>
              <div>
                <input
                  type="text"
                  class="w-full text-4xl placeholder-gray-400 leading-0 font-semibold"
                  placeholder="Type a person to shoutout"
                />
              </div>
            </div>
            <div class="card-body divide-y divide-y-reverse divide-gray-200">
              <div class="flex items-center py-3">
                <img
                  src="../assets/images/coin-icon.svg"
                  width="25"
                  height="25"
                  class="h-8 w-8 mr-2 rounded-full border-2 border-white"
                />
                <input
                  type="text"
                  class="w-full text-xl placeholder-gray-400 leading-0 font-normal"
                  placeholder="Add gold (optional)"
                />
              </div>
              <div class="flex items-center py-2">
                <div class="text-xl text-gray-500">Select a core value</div>
                <hr />
              </div>
            </div>
            <div class="card-footer my-4">
              <input
                type="text"
                class="w-full placeholder-gray-400 leading-0 font-normal"
                placeholder="Give them a meaningful message"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.shoutby:after {
  border-left: 10px solid #000;
}
</style>
