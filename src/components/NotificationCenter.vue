<template>
  <div
    class="
      notification-center
      absolute
      bg-white bg-opacity-80
      dark:bg-gray-600 dark:bg-opacity-50
      backdrop-filter backdrop-blur-lg
      duration-150
      flex flex-col
    "
    :class="{ show: isOpen }"
  >
    <div
      :class="darkMode ? 'border border-gray-700' : 'border-t border-b border-gray-300'"
      class="flex flex-col text-2xs p-3 text-gray-600 dark:text-gray-200">
      <p class="text-right pt-1">
        Manage notifications
      </p>
      <button
        class="
          absolute
          top-0
          mt-1
          rounded-full
          text-left
          bg-white
          dark:bg-gray-700 dark:text-white
          p-2
          border border-gray-200
          dark:border-gray-600
          duration-150
        "
      >
        <img
          src="@/../public/restore.svg"
          width="14"
          class="duration-150"
          :class="{ 'filter invert': darkMode }"
        />
      </button>
    </div>
    <div
      :class="{ 'bg-gray-900': darkMode }"
      class="h-screen flex justify-start"
    >
      <div class="notify-center overflow-y-scroll grid grid-cols-1">
        <!-- Card -->
        <a
          dir="rtl"
          v-for="(item, index) in notifications"
          :key="index"
          href="#"
          :class="darkMode ? 'border border-gray-700' : 'border'"
          class="
            dark:bg-gray-600 dark:bg-opacity-50
            bg-slate-900
            px-5
            py-2
            shadow
          "
        >
          <p class="text-xs text-gray-500 mb-3">
            {{ item.messageType }}
          </p>
          <!-- Header -->
          <div class="flex flex-row">
            <img src="https://picsum.photos/40/40" class="rounded" />
            <p
              :class="!darkMode ? 'text-gray-600 ' : ''"
              class="text-gray-200 mr-2"
            >
              {{ item.title }}
            </p>
          </div>

          <!-- Content -->
          <p class="text-xs text-gray-500 mt-3">
            {{ item.description }}
          </p>
          <p dir="rtl" class="text-left text-xs text-gray-500 mt-3">
            {{ item.date }}
          </p>
        </a>
      </div>
    </div>
    <div
      :class="darkMode ? 'border border-gray-700' : 'border-t border-b border-gray-300'"
      class="control-center grid w-full grid-cols-4 gap-1 p-4 bg-white bg-opacity-80
      dark:bg-gray-600 fixed bottom-0 "
    >
      <button
        class="
          flex flex-col
          items-start
          gap-3
          bg-white
          dark:bg-gray-700 dark:text-white
          px-1
          pt-2
          pb-1
          border border-gray-200
          dark:border-gray-600
          duration-150
        "
        v-for="(item, index) in controls"
        :key="index"
        @click="
          item.active = !item.active;
          item.click();
        "
        :class="{
          'bg-blue-600 dark:bg-blue-500 text-white border-blue-600 dark:border-blue-500':
            item.active,
        }"
      >
        <img
          :src="item.icon"
          width="14"
          class="duration-150"
          :class="{ 'filter invert': item.active || darkMode }"
        />
        <span>{{ item.label }}</span>
      </button>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  name: "NotificationCenter",
  computed: {
    ...mapState({
      isOpen: (state) => state.notificationCenterOpen,
      darkMode: (state) => state.darkMode,
      nightLight: (state) => state.nightLight,
    }),
  },
  data() {
    return {
      notifications: [
        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },
        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },
        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },

        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },

        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },
        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },
        {
          title: "نحوه ذخیره گیری هزینه ها در شعب و مدیریت شع",
          description: "	اطلاعیه 2/10401 اداره کل حسابداری مالی",
          date: "1398/11/01 15:12:11",
          messageType: "	اداره کل حسابداری مالی",
        },
      ],
      controls: [],
    };
  },
  methods: {
    initItems() {
      this.controls = [
        // { label: 'Location', icon: require('@/assets/ui/location.png'), active: false, click: this.none },
        // { label: 'Battery saver', icon: require('@/assets/ui/battery-saver.png'), active: true, click: this.none },
        {
          label: "Night light",
          icon: require("@/assets/ui/night-light.png"),
          active: this.nightLight,
          click: this.toggleNightLight,
        },
        // { label: 'Bluetooth', icon: require('@/assets/ui/bluetooth.png'), active: true, click: this.none },
        // { label: 'Offline mode', icon: require('@/assets/ui/offline-mode.png'), active: false, click: this.none },
        // { label: 'Connect', icon: require('@/assets/ui/connect.png'), active: false, click: this.none },
        // { label: 'Project', icon: require('@/assets/ui/project.png'), active: false, click: this.none },
        // { label: 'Network', icon: require('@/assets/ui/network.png'), active: false, click: this.none },
        // { label: 'Sharing', icon: require('@/assets/ui/sharing.png'), active: false, click: this.none },
        // { label: 'Tablet mode', icon: require('@/assets/ui/tablet-mode.png'), active: false, click: this.none },
        // { label: 'Security', icon: require('@/assets/ui/security.png'), active: false, click: this.none },
        {
          label: "Dark mode",
          icon: require("@/assets/ui/focus-assist.png"),
          active: this.darkMode,
          click: this.toggleDarkMode,
        },
      ];
    },
    toggleDarkMode() {
      this.$store.dispatch("toggleDarkMode");
    },
    toggleNightLight() {
      this.$store.dispatch("toggleNightLight");
    },
    none() {},
  },
  mounted() {
    this.initItems();
  },
};
</script>

<style lang="scss">
.notification-center {
  width: 320px;
  top: 0;
  right: -340px;
  bottom: 40px;
  box-shadow: -6px 0 6px #0001;
}

.notification-center.show {
  right: 0;
}

.control-center {
  button {
    font-size: 9px;
    border-radius: 4px;
  }
}
.notify-center {
  height: calc(100vh - 162px) !important;
  align-content: baseline;
}
.notify-center {
  -ms-overflow-style: none; // Internet Explorer 10+
  scrollbar-width: none; // Firefox
}
.notify-center::-webkit-scrollbar {
  display: none; // Safari and Chrome
}
</style>
