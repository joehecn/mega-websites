<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { useDark } from '@vueuse/core'

interface Site {
  name: string
  image: string
  url: string
  abbreviation: string
}

const isDark = useDark()

const sassSites = ref<Site[]>([])

const sites = [
  // {
  //   name: 'MEGA SASS 平臺',
  //   image:
  //     'https://cbosv3.oss-cn-hongkong.aliyuncs.com/saas/users/91/V2VjaGF0SU1HMzU5LmpwZw==?x-oss-process=image/resize,w_200',
  //   url: 'https://saas.cloud-building.com/',
  // },
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

onMounted(() => {
  // Fetch SASS sites from the API
  fetch('https://saas.cloud-building.com/api/v1/bp/internal/public/listOrganization')
    .then(response => response.json())
    .then(data => {
      sassSites.value = data.data.list.map((item: { name: string, abbreviation: string, image: string }) => ({
        name: item.name,
        image: `https://cbosv3.oss-cn-hongkong.aliyuncs.com/${item.image}?x-oss-process=image/resize,w_200`,
        url: `https://saas.cloud-building.com/${item.abbreviation}`,
        abbreviation: item.abbreviation,
      }))
    })
    .catch(error => {
      console.error('Error fetching SASS sites:', error)
    })
})
</script>

<template>
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
        <h1 class="title">MEGA SASS 平臺 <el-link href="https://saas.cloud-building.com/" target="_blank"
            type="primary">https://saas.cloud-building.com/</el-link></h1>
        <el-row>
          <el-col v-for="site in sassSites" :key="site.url" :xs="24" :sm="12" :md="8" :lg="6" :xl="4">
            <div class="card-wrapper">
              <el-card>
                <template #header>
                  <div class="card-header">
                    <span class="ellipsis">{{ site.name }}</span>
                  </div>
                </template>
                <div class="image-wrapper">
                  <img :src="site.image" loading="lazy" style="width: 100%; height: 100%" />
                </div>
                <template #footer>
                  <el-link :href="site.url" target="_blank" type="primary">{{ `https://.../${site.abbreviation}`
                  }}</el-link>
                </template>
              </el-card>
            </div>
          </el-col>
        </el-row>

        <div style="height: 24px;"></div>
        <h1 class="title">其它平臺</h1>
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
.ellipsis {
  display: inline-block;
  /* 或 block，根据布局需要 */
  max-width: 100%;
  /* 设置最大宽度，根据实际需求调整 */
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  vertical-align: bottom;
  /* 可选，优化对齐 */
}

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
