<script setup>
import { Icon } from "@iconify/vue";
import { ref } from "vue";
import { useNavbarStore } from "../stores/store";
import { storeToRefs } from "pinia";

const store = useNavbarStore();
const { setActiveToLost, setActiveToFound } = store;
const { activeHeaderLink } = storeToRefs(store);

const profileDropdown = ref(false);
</script>

<template>
  <header class="bg-[#FFF6DB] shadow">
    <div
      class="max-w-7xl mx-auto px-2 sm:px-4 lg:divide-y lg:divide-gray-200 lg:px-8"
    >
      <div class="relative h-16 flex justify-between">
        <div class="relative z-10 px-2 flex lg:px-0">
          <div class="flex-shrink-0 flex items-center">
            <!-- <img
                            class="block h-8 w-auto"
                            src="https://tailwindui.com/img/logos/workflow-mark-indigo-600.svg"
                            alt="Workflow"
                        /> -->
            <a href="/" class="text-xl font-semibold italic">Lost & Found</a>
          </div>
        </div>
        <div
          class="relative z-0 flex-1 px-2 flex items-center justify-center sm:absolute sm:inset-0"
        >
          <div class="w-full sm:max-w-xs">
            <label for="search" class="sr-only">Search</label>
            <div class="relative">
              <div
                class="pointer-events-none absolute inset-y-0 left-0 pl-3 flex items-center"
              >
                <!-- Heroicon name: solid/search -->
                <svg
                  class="h-5 w-5 text-gray-400"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  aria-hidden="true"
                >
                  <path
                    fill-rule="evenodd"
                    d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
                    clip-rule="evenodd"
                  />
                </svg>
              </div>
              <input
                id="search"
                name="search"
                class="block w-full bg-white border border-gray-300 rounded-md py-2 pl-10 pr-3 text-sm placeholder-gray-500 focus:outline-none focus:text-gray-900 focus:placeholder-gray-400 focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                placeholder="Search"
                type="search"
              />
            </div>
          </div>
        </div>
        <div class="relative z-10 flex items-center lg:hidden">
          <!-- Mobile menu button -->
          <button
            type="button"
            class="rounded-md p-2 inline-flex items-center justify-center text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500"
            aria-controls="mobile-menu"
            aria-expanded="false"
          >
            <span class="sr-only">Open menu</span>
            <!--
            Icon when menu is closed.

            Heroicon name: outline/menu

            Menu open: "hidden", Menu closed: "block"
          -->
            <svg
              class="block h-6 w-6"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              aria-hidden="true"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
            </svg>
            <!--
            Icon when menu is open.

            Heroicon name: outline/x

            Menu open: "block", Menu closed: "hidden"
          -->
            <svg
              class="hidden h-6 w-6"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              aria-hidden="true"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
        <div class="hidden lg:relative lg:z-10 lg:ml-4 lg:flex lg:items-center">
          <button
            type="button"
            class="flex-shrink-0 bg-white rounded-full p-1 text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
          >
            <span class="sr-only">View notifications</span>
            <!-- Heroicon name: outline/bell -->
            <svg
              class="h-6 w-6"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              aria-hidden="true"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"
              />
            </svg>
          </button>

          <!-- Profile dropdown -->
          <div class="flex-shrink-0 relative ml-4">
            <div>
              <button
                @click="profileDropdown = !profileDropdown"
                class="bg-white rounded-full flex focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                id="user-menu-button"
                aria-expanded="false"
                aria-haspopup="true"
              >
                <span class="sr-only">Open user menu</span>
                <img class="h-8 w-8 rounded-full" src="/profile.png" alt="" />
              </button>
            </div>
            <div
              v-show="profileDropdown"
              class="origin-top-right absolute right-0 mt-2 w-48 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 py-1 focus:outline-none"
              role="menu"
              aria-orientation="vertical"
              aria-labelledby="user-menu-button"
              tabindex="-1"
            >
              <!-- Active: "bg-gray-100", Not Active: "" -->
              <a
                href="#"
                class="block py-2 px-4 text-sm text-gray-700"
                role="menuitem"
                tabindex="-1"
                id="user-menu-item-0"
                >Your Profile</a
              >

              <a
                href="#"
                class="block py-2 px-4 text-sm text-gray-700"
                role="menuitem"
                tabindex="-1"
                id="user-menu-item-1"
                >Settings</a
              >

              <a
                href="#"
                class="block py-2 px-4 text-sm text-gray-700"
                role="menuitem"
                tabindex="-1"
                id="user-menu-item-2"
                >Sign out</a
              >
            </div>
          </div>
        </div>
      </div>
      <nav class="hidden lg:py-4 lg:flex lg:space-x-8" aria-label="Global">
        <!-- Current: "bg-gray-100 text-gray-900", Default: "text-gray-900 hover:bg-gray-50 hover:text-gray-900" -->
        <button
          :class="
            activeHeaderLink === 'lost'
              ? 'bg-[#F1B380] text-gray-900'
              : 'text-gray-900 hover:bg-[#F1B380] hover:text-gray-900'
          "
          class="rounded-md py-2 px-3 inline-flex items-center text-sm font-medium"
          @click="setActiveToLost"
        >
          Lost Items
        </button>

        <button
          :class="
            activeHeaderLink === 'found'
              ? 'bg-[#F1B380] text-gray-900'
              : 'text-gray-900 hover:bg-[#F1B380] hover:text-gray-900'
          "
          class="rounded-md py-2 px-3 inline-flex items-center text-sm font-medium"
          @click="setActiveToFound"
        >
          Found Items
        </button>
      </nav>
    </div>
  </header>
</template>
