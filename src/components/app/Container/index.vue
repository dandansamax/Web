<template>
  <q-page-container>
    <div :style="containerStyle">
      <router-view v-slot="{ Component }">
        <template v-if="Component">
          <!-- TODO 想加个q-transition--fade，但测试下来有点问题 -->
          <keep-alive :exclude="['CollaboratorList']">
            <component :is="Component"></component>
          </keep-alive>
        </template>
      </router-view>
    </div>
  </q-page-container>
  <!-- 登陆页跳转 -->
  <authentication-guard />
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue'
import AuthenticationGuard from './AuthenticationGuard.vue'
import { useLayout } from '@/components/app/useLayout'

export default defineComponent({
  components: { AuthenticationGuard },
  setup() {
    let layout = useLayout()

    return {
      containerStyle: layout.containerStyle
    }
  }
})
</script>

<style scoped></style>
