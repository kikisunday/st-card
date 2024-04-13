<script setup lang="ts">
const router = useRouter();
const user = {
  id: '1',
};
const drawer = ref<boolean>(false);

const items = [
  {
    title: 'ホーム',
    icon: 'mdi-home',
  },
  {
    title: 'マイキャットカード',
    icon: 'mdi-account',
    color: '',
  },
  {
    title: 'ログアウト',
    icon: 'mdi-logout',
    color: 'red',
  },
];

const onIconClick = (title: string) => {
  switch (title) {
    case 'ホーム':
      router.push(`/`);
      break;
    case 'マイページ':
      router.push(`/mypage/${user.id}`);
      break;
    case 'ログアウト':
      router.push(`/login`);
      break;
  }
};

onMounted(() => {
  console.log();
});
</script>

<template>
  <div>
    <v-app>
      <div class="header">
        <v-app-bar color="primary">
          <template #prepend>
            <v-btn icon="mdi-file-document-check-outline" />
          </template>
          <v-app-bar-title>ホーム</v-app-bar-title>
          <template #append>
            <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
          </template>
        </v-app-bar>
        <v-navigation-drawer v-model="drawer">
          <v-list v-for="item in items" :key="item.title" link>
            <v-list-item
              :prepend-icon="item.icon"
              :title="item.title"
              @click="onIconClick(item.title)"
            />
          </v-list>
          <!-- <template #append>
            <div>asdasd</div>
          </template> -->
        </v-navigation-drawer>
      </div>
      <div class="content">
        <slot />
      </div>
    </v-app>
  </div>
</template>

<style></style>
