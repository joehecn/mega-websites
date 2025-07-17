<script setup lang="ts">
import { useDark } from '@vueuse/core'

const isDark = useDark()

const sites = [
  {
    name: 'MEGA SASS 平臺',
    image:
      'https://cbosv3.oss-cn-hongkong.aliyuncs.com/saas/users/91/V2VjaGF0SU1HMzU5LmpwZw==?x-oss-process=image/resize,w_200',
    url: 'https://saas.cloud-building.com/',
  },
  {
    name: '書院管理系統',
    image: 'https://woosing.cloud-building.com/assets/login-home-ef73171b.jpg',
    url: 'https://woosing.cloud-building.com/',
  },
  {
    name: '物業管理系統',
    image: 'https://fm.cloud-building.com/img/megaBackground-min.png',
    url: 'https://fm.cloud-building.com/',
  },
  {
    name: '設備管理平臺',
    image: '/mega-websites/img/cbos.png',
    url: 'https://cbosv3.cloud-building.com/',
  },
  {
    name: 'MEGA2.0 系統',
    image: '/mega-websites/img/mega.png',
    url: 'https://mega.cloud-building.com/',
  },
  {
    name: 'CORE2.0 系統',
    image: 'https://core.cloud-building.com/before.810109a8250bc37e3828.png',
    url: 'https://core.cloud-building.com/',
  },
  {
    name: '太古地產能源管理',
    image: '/mega-websites/img/swire.png',
    url: 'https://swire.enermon.cloud/',
  },
  {
    name: '裕華國際大廈能源管理',
    image: '/mega-websites/img/yuehwa.png',
    url: 'http://yuehwa.megabuilding.net/',
  },
  {
    name: 'MEGA 官網',
    image: 'https://www.mega-automation.com/images/banner_home.png',
    url: 'https://www.mega-automation.com/',
  },
  {
    name: '凝方科技官網',
    image: '/mega-websites/img/fusquare.png',
    url: 'http://www.fusquare.com/',
  },
]
</script>

<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView /> -->
  <el-config-provider>
    <el-container>
      <el-header>
        <el-switch size="large" v-model="isDark" inline-prompt>
          <template #active-action>
            <i-ep-moon />
          </template>
          <template #inactive-action>
            <i-ep-sunny />
          </template>
        </el-switch>
      </el-header>
      <el-main>
        <el-row>
          <el-col v-for="site in sites" :key="site.url" :xs="24" :sm="12" :md="8" :lg="6" :xl="4">
            <div class="card-wrapper">
              <el-card>
                <template #header>
                  <div class="card-header">
                    <span>{{ site.name }}</span>
                  </div>
                </template>
                <div class="image-wrapper">
                  <img :src="site.image" loading="lazy" style="width: 100%; height: 100%" />
                </div>
                <template #footer>
                  <el-link :href="site.url" target="_blank" type="primary">{{ site.url }}</el-link>
                </template>
              </el-card>
            </div>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </el-config-provider>
</template>

<style scoped>
.card-wrapper {
  margin: 10px;
}

.image-wrapper {
  width: 100%;
  position: relative;
  padding-top: 50%;
  /* 1:1 宽高比 */
  overflow: hidden;
}

.image-wrapper img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>

<!-- <style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> -->
