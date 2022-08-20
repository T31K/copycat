<template>
  <div class="relative bg-yellow-50 overflow-hidden max-h-screen">
    <header
      class="fixed right-0 top-0 left-60 bg-yellow-50 py-3 px-4 h-16 draggable"
    >
      <div class="max-w-4xl mx-auto">
        <div class="flex items-center justify-between">
          <div>
            <button
              type="button"
              class="flex items-center focus:outline-none rounded-lg text-gray-600 hover:text-yellow-600 focus:text-yellow-600 font-semibold p-2 border border-transparent hover:border-yellow-300 focus:border-yellow-300 transition"
            >
              <span
                class="inline-flex items-center justify-center w-6 h-6 text-gray-600 text-xs rounded bg-white transition mr-2"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="1em"
                  height="1em"
                  fill="currentColor"
                  class="bi bi-chevron-left"
                  viewBox="0 0 16 16"
                >
                  <path
                    fill-rule="evenodd"
                    d="M11.354 1.646a.5.5 0 0 1 0 .708L5.707 8l5.647 5.646a.5.5 0 0 1-.708.708l-6-6a.5.5 0 0 1 0-.708l6-6a.5.5 0 0 1 .708 0z"
                  />
                </svg>
              </span>
              <span class="text-sm">Archive</span>
            </button>
          </div>
          <div class="text-lg font-bold">Today's Plan</div>
          <div>
            <button
              type="button"
              class="flex items-center focus:outline-none rounded-lg text-gray-600 hover:text-yellow-600 focus:text-yellow-600 font-semibold p-2 border border-transparent hover:border-yellow-300 focus:border-yellow-300 transition"
            >
              <span class="text-sm">This week</span>
              <span
                class="inline-flex items-center justify-center w-6 h-6 text-gray-600 text-xs rounded bg-white transition ml-2"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="1em"
                  height="1em"
                  fill="currentColor"
                  class="bi bi-chevron-right"
                  viewBox="0 0 16 16"
                >
                  <path
                    fill-rule="evenodd"
                    d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z"
                  />
                </svg>
              </span>
            </button>
          </div>
        </div>
      </div>
    </header>

    <aside
      class="fixed inset-y-0 left-0 bg-white shadow-md max-h-screen w-60 overflow-y-auto"
    >
      <div class="flex flex-col justify-between h-full">
        <div class="flex-grow">
          <div class="px-4 py-6 text-center border-b">
            <h1 class="text-xl font-bold leading-none">
              <span class="text-yellow-700">Task Manager</span> App
            </h1>
          </div>
          <div class="p-4">
            <ul class="space-y-1">
              <li
                v-for="(item, key) in [
                  1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 3, 4, 1, 2, 3, 4,
                ]"
                :key="key"
              >
                <a
                  href="javascript:void(0)"
                  class="flex items-center bg-yellow-200 rounded-xl font-bold text-sm text-yellow-900 py-3 px-4"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="1em"
                    height="1em"
                    fill="currentColor"
                    class="text-lg mr-4"
                    viewBox="0 0 16 16"
                  >
                    <path
                      d="M4 .5a.5.5 0 0 0-1 0V1H2a2 2 0 0 0-2 2v1h16V3a2 2 0 0 0-2-2h-1V.5a.5.5 0 0 0-1 0V1H4V.5zM16 14V5H0v9a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2zm-3.5-7h1a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-1a.5.5 0 0 1-.5-.5v-1a.5.5 0 0 1 .5-.5z"
                    /></svg
                  >Plan
                </a>
              </li>
            </ul>
          </div>
        </div>
        <div class="p-4">
          <button
            type="button"
            class="inline-flex items-center justify-center h-9 px-4 rounded-xl bg-gray-900 text-gray-300 hover:text-white text-sm font-semibold transition"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="1em"
              height="1em"
              fill="currentColor"
              class=""
              viewBox="0 0 16 16"
            >
              <path
                d="M12 1a1 1 0 0 1 1 1v13h1.5a.5.5 0 0 1 0 1h-13a.5.5 0 0 1 0-1H3V2a1 1 0 0 1 1-1h8zm-2 9a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"
              />
            </svg>
          </button>
          <span class="font-bold text-sm ml-2">Settings</span>
        </div>
      </div>
    </aside>

    <main class="ml-60 pt-[11vh] px-10 max-h-screen bg-white overflow-auto">
      <div class="border rounded-lg h-[85vh]" id="code">
        <div v-for="(item, key) in list" :key="key">
          <pre><code class="language-markup">
              <div>{{item}} </div>
              </code></pre>
        </div>
      </div>
    </main>
  </div>
</template>
