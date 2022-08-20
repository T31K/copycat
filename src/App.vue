<template>
  <div class="relative bg-yellow-50 overflow-hidden max-h-screen">
    <header
      class="fixed right-0 top-0 left-0 bg-yellow-50 py-3 px-4 h-16 draggable"
    >
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
        <input type="text" />
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
    </header>

    <aside
      class="fixed inset-y-0 left-0 bg-gray-100 max-h-screen w-[13em] overflow-y-auto top-[70px]"
    >
      <div class="flex flex-col justify-between h-full">
        <div class="px-2 py-4">
          <ul class="space-y-1">
            <li v-for="(item, key) in navList" :key="key">
              <a
                href="javascript:void(0)"
                class="flex items-center bg-gray-200 rounded-md font-bold text-sm text-gray-700 px-4"
              >
                <span class="text-lg mr-2">🌈</span>
                {{ item.label }}
              </a>
            </li>
          </ul>
        </div>
      </div>
    </aside>
    <aside
      class="fixed inset-y-0 left-[13em] w-[13em] bg-gray-50 max-h-screen w-50 overflow-y-auto top-[70px] overflow-hidden"
    >
      <div class="flex flex-col justify-between h-full">
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
    </aside>

    <main
      class="ml-[25rem] pt-5 px-10 max-h-screen bg-white overflow-auto mt-[70px]"
    >
      <div class="border rounded-xl h-[85vh]" id="code">
        <div v-for="(item, key) in list" :key="key">
          <CodeEditor
            v-model="hello"
            language_selector
            :languages="[
              ['javascript', 'JS'],
              ['cpp', 'C++'],
              ['python', 'Python'],
            ]"
            width="100%"
            height="500px"
            :wrap_code="true"
          ></CodeEditor>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import CodeEditor from "simple-code-editor";

export default {
  name: "App",
  components: { CodeEditor },
  data() {
    return {
      list: ["hello"],
      hello: "console.log('hello')",
      navList: [{ label: "New" }, { label: "Favourites" }],
    };
  },
  mounted() {
    this.receiveMessage();
  },
  methods: {
    receiveMessage() {
      window.ipcRenderer.receive("defaultChannel", (message) => {
        this.list.push(message);
        console.log(message); // Prints 'whoooooooh!'
      });
    },
  },
};
</script>

<style>
pre {
  background: none !important;
  margin: 0 !important;
}

div#code {
  background: #222;
}

code {
  text-shadow: none;
}

.draggable {
  -webkit-user-select: none;
  user-select: none;
  -webkit-app-region: drag;
}
.bg-red {
  background: red;
  height: 90vh;
}
.bg-blue {
  background: blue;
  height: 90vh;
}

#nav {
  background: #222;
  height: 5vh;
  padding: 10px 50px;
  padding-left: 10px;
  padding-right: 25px;
  display: flex;
}

span#red {
  background-color: #e4514f;
  border-radius: 50%;
  height: 15px;
  width: 15px;
  display: inline-block;
  margin-left: 10px;
}

::-webkit-scrollbar-button {
  background: #ccc;
}
::-webkit-scrollbar-track-piece {
  background: none;
}
::-webkit-scrollbar-thumb {
  background: #eee;
}
</style>
