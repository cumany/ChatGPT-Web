<!--
 * @Author: cumany cuman@qq.com
 * @Date: 2023-03-08 13:50:24
 * @LastEditors: cumany cuman@qq.com
 * @LastEditTime: 2023-03-12 21:39:46
 * @FilePath: \ChatGPT-Web\src\components\common\UserAvatar\index.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup lang='ts'>
import { computed } from 'vue'
import { useUserStore } from '@/store'

import { isString } from '@/utils/is'

const userStore = useUserStore()

const userInfo = computed(() => userStore.userInfo)
</script>

<template>
  <div class="flex items-center">
    <div class="w-10 h-10 text-4xl overflow-hidden rounded-full">
      <template v-if="isString(userInfo.avatar) && userInfo.avatar.length > 0">
        {{ userInfo.avatar }}
      </template>
      <template v-else>
        🪐
      </template>
    </div>
    <div class="ml-2">
      <h2 class="font-bold text-md">
        {{ userInfo.name ?? 'chat' }}
      </h2>
      <p class="overflow-hidden text-xs text-gray-500 text-ellipsis whitespace-nowrap">
        <span
          v-if="isString(userInfo.description) && userInfo.description !== ''"
          v-html="userInfo.description"
        />
      </p>
    </div>
  </div>
</template>
