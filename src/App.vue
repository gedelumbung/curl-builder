<template>
  <div id="app">
    <div class="container mx-auto">
      <div class="bg-white p-12 my-10 relative">
        <div
          class="icon bg-blue-600 text-white w-6 h-6 absolute flex items-center justify-center p-5"
          style="left:-40px"
        >
          <i
            class="fal fa-phone-volume fa-fw text-2xl transform -rotate-45"
          ></i>
        </div>
        <h3 class="text-2xl text-gray-900 font-semibold">
          CURL Command Builder
        </h3>
        <p class="text-gray-600">Simple thing, but this we always forget :p</p>

        <input
          type="tel"
          name=""
          id=""
          placeholder="URL"
          class="border p-2 w-full space-x-5 mt-5"
        />
        <select class="block appearance-none w-full bg-white border p-2 w-full mt-3">
          <option>-- HTTP METHOD --</option>
          <option>GET</option>
          <option>POST</option>
          <option>PUT</option>
          <option>DELETE</option>
          <option>PATCH</option>
        </select>
        <textarea
          name=""
          id=""
          cols="10"
          rows="3"
          placeholder="Tell us about desired property"
          class="border p-2 mt-3 w-full"
        ></textarea>
      </div>
    </div>
  </div>
</template>
