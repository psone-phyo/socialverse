<template>
    <div class="md:flex justify-center bg-gray-200 hidden">
        <div class="grid grid-cols-7 lg:grid-cols-9 w-full xl:w-8/12 lg:mx-0 mx-10 lg:order-0">
                <div class="lg:col-span-2 lg:block  hidden">
                    <div class="card flex justify-end fixed top-0 ">
                        <Menu :model="items" class="" />
                    </div>
                </div>
            <div class="col-span-5 flex flex-column justify-center items-center lg:order-1 order-2">
                <slot/>
            </div>

            <div class="col-span-2 flex justify-end mr-[10%] lg:order-2">
                <div class="card flex justify-start fixed top-0">
                <Menu :model="items" class="lg:ml-[10%]">
                    <template #start>
                        <span class="inline-flex items-center gap-1 px-2 py-2">
                            <svg width="35" height="40" viewBox="0 0 35 40" fill="none" xmlns="http://www.w3.org/2000/svg" class="h-8">
                                <path
                                    d="M25.87 18.05L23.16 17.45L25.27 20.46V29.78L32.49 23.76V13.53L29.18 14.73L25.87 18.04V18.05ZM25.27 35.49L29.18 31.58V27.67L25.27 30.98V35.49ZM20.16 17.14H20.03H20.17H20.16ZM30.1 5.19L34.89 4.81L33.08 12.33L24.1 15.67L30.08 5.2L30.1 5.19ZM5.72 14.74L2.41 13.54V23.77L9.63 29.79V20.47L11.74 17.46L9.03 18.06L5.72 14.75V14.74ZM9.63 30.98L5.72 27.67V31.58L9.63 35.49V30.98ZM4.8 5.2L10.78 15.67L1.81 12.33L0 4.81L4.79 5.19L4.8 5.2ZM24.37 21.05V34.59L22.56 37.29L20.46 39.4H14.44L12.34 37.29L10.53 34.59V21.05L12.42 18.23L17.45 26.8L22.48 18.23L24.37 21.05ZM22.85 0L22.57 0.69L17.45 13.08L12.33 0.69L12.05 0H22.85Z"
                                    fill="var(--p-primary-color)"
                                />
                                <path
                                    d="M30.69 4.21L24.37 4.81L22.57 0.69L22.86 0H26.48L30.69 4.21ZM23.75 5.67L22.66 3.08L18.05 14.24V17.14H19.7H20.03H20.16H20.2L24.1 15.7L30.11 5.19L23.75 5.67ZM4.21002 4.21L10.53 4.81L12.33 0.69L12.05 0H8.43002L4.22002 4.21H4.21002ZM21.9 17.4L20.6 18.2H14.3L13 17.4L12.4 18.2L12.42 18.23L17.45 26.8L22.48 18.23L22.5 18.2L21.9 17.4ZM4.79002 5.19L10.8 15.7L14.7 17.14H14.74H15.2H16.85V14.24L12.24 3.09L11.15 5.68L4.79002 5.2V5.19Z"
                                    fill="var(--p-text-color)"
                                />
                            </svg>
                            <span class="text-xl font-semibold">PRIME<span class="text-primary">APP</span></span>
                        </span>
                    </template>
                    <template #submenulabel="{ item }">
                        <span class="text-primary font-bold">{{ item.label }}</span>
                    </template>
                    <template #item="{ item, props }">
                        <a v-ripple class="flex items-center" v-bind="props.action">
                            <span :class="item.icon" />
                            <span>{{ item.label }}</span>
                            <Badge v-if="item.badge" class="ml-auto bg-primary" :value="item.badge" />
                            <span v-if="item.shortcut" class="ml-auto border border-surface rounded bg-emphasis text-muted-color text-xs p-1">{{ item.shortcut }}</span>
                        </a>
                    </template>
                    <template #end>
                        <button v-ripple class="relative overflow-hidden w-full border-0 bg-transparent flex items-start p-2 pl-4 hover:bg-surface-100 dark:hover:bg-surface-800 rounded-none cursor-pointer transition-colors duration-200">
                            <Avatar image="https://primefaces.org/cdn/primevue/images/avatar/amyelsner.png" class="mr-2" shape="circle" />
                            <span class="inline-flex flex-col items-start">
                                <span class="font-bold">Amy Elsner</span>
                                <span class="text-sm">Admin</span>
                            </span>
                        </button>
                    </template>
                </Menu>
                </div>
            </div>
        </div>
    </div>

    <!-- for Mobile -->
    <div class="block md:hidden">
        <v-app >
      <!-- Top Navigation Bar -->
      <v-card >
    <v-layout class="">
      <v-app-bar
        color="#eeeeee"
        prominent
      >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>My files</v-toolbar-title>

        <v-spacer></v-spacer>
        <div class=" mr-5 flex items-center justify-between gap-5">
            <button ><i class="fa-solid fa-magnifying-glass text-lg"></i></button>
            <button ><i class="fa-solid fa-comment-sms text-xl"></i></button>
        </div>

      </v-app-bar>

      <v-navigation-drawer
        v-model="drawer"
        :location="undefined"
        temporary
        color="#eeeeee"
      >
        <v-list>
            <button class="hover:bg-dark border border-white w-full p-1">
                Setting
            </button>
            <hr class="w-3/4 mx-auto mb-2">

            <button class="hover:bg-dark border border-white w-full p-1">
                Setting
            </button>
            <hr class="w-3/4 mx-auto mb-2">

            <button class="hover:bg-dark border border-white w-full p-1">
                Setting
            </button>
            <hr class="w-3/4 mx-auto mb-2">

        </v-list>
      </v-navigation-drawer>
      <v-main class="mt-1">
        <slot></slot>
      </v-main>
    </v-layout>
  </v-card>

      <!-- Main Content -->


      <!-- Bottom Navigation Bar -->
        <v-bottom-navigation color="primary" active class="bg-[#eeeeee]">
          <v-btn>
            <i class="fa-solid fa-house text-lg"></i>
            Home
          </v-btn>
          <v-btn>
            <i class="fa-solid fa-plus text-lg"></i>
            Create
          </v-btn>
          <v-btn>
            <i class="fa-solid fa-bell text-lg"></i>
            Notification
          </v-btn>
          <v-btn>
            <i class="fa-solid fa-circle-user text-lg"></i>
            Profile
          </v-btn>
        </v-bottom-navigation>
    </v-app>
    </div>
</template>

<script setup>
import moment from "moment";
import { ref } from "vue";
import { router } from '@inertiajs/vue3'
//components
import Mobile from '@/Pages/layout/mobile.vue'
//primevue
import Menu from 'primevue/menu';
import Avatar from 'primevue/avatar';
import Badge from 'primevue/badge';
const items = ref([
    {
        separator: true
    },
    {
        label: 'Documents',
        items: [
            {
                label: 'Home    ',
                icon: 'pi pi-search',
                command: () => router.get(route('home'))
            },
            {
                label: 'Create New Post',
                icon: 'pi pi-plus',
                command: () => router.get(route('post'))
            },
            {
                label: 'Search',
                icon: 'pi pi-search',
                shortcut: '⌘+S'
            },
            {
                label: 'Profile',
                icon: 'pi pi-search',
                command: () => router.get(route('profile'))
            }
        ]
    },
    {
        label: 'Profile',
        items: [
            {
                label: 'Settings',
                icon: 'pi pi-cog',
                shortcut: '⌘+O'
            },
            {
                label: 'Messages',
                icon: 'pi pi-inbox',
                badge: 2
            },
            {
                label: 'Logout',
                icon: 'pi pi-sign-out',
                command: () => router.post(route('logout'))
            }
        ]
    },
    {
        separator: true
    }
]);

const drawer = ref(false);
</script>
