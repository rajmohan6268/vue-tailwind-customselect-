<template>
  <div class="justify-center flex w-full mt-20 pointer">
    <Listbox
      class="w-56 "
      v-model="selectedWrestler"
      :items="wrestlers"
      v-slot="{ isOpen, components }"
    >
      <contextual-component :use="components.label" class="sr-only">
        Select a wrestler
      </contextual-component>

      <contextual-component
        :use="components.button"
        class="rounded flex items-center justify-between  p-1 w-56 border"
      >
        <div class="flex items-center">
          <img
            v-if="selectedWrestler.img"
            class="h-6 w-6 rounded-full"
            :src="selectedWrestler.img"
          />
          <span v-if="selectedWrestler.name" class="ml-2 font-medium">
            {{ selectedWrestler.name }}</span
          >
        </div>
        <div
          v-show="selectedWrestler.name"
          class="bg-green-400 my-auto flex items-center rounded-full h-3 w-3"
        />
        <v-else
          v-show="!selectedWrestler.name"
          class="flex items-center  justify-between w-full"
        >
          <!-- <img class="h-6 w-6 rounded-full bg-black" src="" /> -->
          <div class="flex">
            <div class="h-6 w-6    rounded-full bg-gray-300 " />
            <div class="ml-2 font-medium">slect a user</div>
          </div>
          <span>
            <svg
              class="h-5 w-5 text-gray-800"
              x-description="Heroicon name: selector"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
              aria-hidden="true"
            >
              <path
                fill-rule="evenodd"
                d="M10 3a1 1 0 01.707.293l3 3a1 1 0 01-1.414 1.414L10 5.414 7.707 7.707a1 1 0 01-1.414-1.414l3-3A1 1 0 0110 3zm-3.707 9.293a1 1 0 011.414 0L10 14.586l2.293-2.293a1 1 0 011.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z"
                clip-rule="evenodd"
              ></path></svg
          ></span>
        </v-else>
      </contextual-component>

      <contextual-component
        transition:leave="transition ease-in duration-300"
        transition:leave-start="opacity-100"
        transition:leave-end="opacity-0"
        class="mt-1 h-40 overflow-y-auto focus:outline-none border border-gray-500  rounded-sm "
        :use="components.list"
        v-show="isOpen"
        v-slot="{ item }"
      >
        <contextual-component
          :use="components.option"
          :value="item"
          v-slot="{ isActive, isSelected }"
        >
          <!-- v-slot="{ isActive, isSelected }" -->

          <div
            class="p-1 flex  justify-between"
            :class="
              isActive ? 'bg-indigo-400 text-white' : 'bg-white text-gray-900'
            "
          >
            <div
              :class="isSelected ? 'font-medium' : 'font-normal'"
              class="flex items-center  "
            >
              <img class="h-6 w-6  mr-2  rounded-full" :src="item.img" />
              {{ item.name }}
            </div>
            <!-- <div
              v-show="isSelected"
              class="bg-green-400 my-auto flex items-center rounded-full h-3 w-3"
            /> -->

            <svg
              v-show="isSelected"
              class="h-5 w-5"
              fill="currentColor"
              viewBox="0 0 20 20"
            >
              <path
                fill-rule="evenodd"
                d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </div>
        </contextual-component>
      </contextual-component>
    </Listbox>
  </div>
</template>

<script>
import Listbox from "@/components/Listbox.vue";
export default {
  components: {
    Listbox
  },
  data() {
    return {
      selectedWrestler: "selct",
      slectedimg: "",
      wrestlers: [
        {
          name: "example user a",
          img:
            "https://images.unsplash.com/photo-1491528323818-fdd1faba62cc?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user b",
          img:
            "https://images.unsplash.com/photo-1550525811-e5869dd03032?ixlib=rb-1.2.1&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user c",
          img:
            "https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2.25&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user d",
          img:
            "https://images.unsplash.com/photo-1561505457-3bcad021f8ee?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user e",
          img:
            "https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user f",
          img:
            "https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user g",
          img:
            "https://images.unsplash.com/photo-1487412720507-e7ab37603c6f?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user h",
          img:
            "https://images.unsplash.com/photo-1568409938619-12e139227838?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        },
        {
          name: "example user i",
          img:
            "https://images.unsplash.com/photo-1531427186611-ecfd6d936c79?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=2&amp;w=256&amp;h=256&amp;q=80"
        }
      ]
    };
  }
};
</script>
