<template>
  <footer class="footer">
    Copyright ©
    <span v-if="year">&nbsp;{{ year }}&nbsp;-&nbsp;</span>
    {{ currentYear }} {{ name }}
    <span v-if="siteIcp">
      &nbsp;&amp;&nbsp;
      <a href="https://beian.miit.gov.cn" target="_blank">
        {{ siteIcp }}
      </a>
    </span>
  </footer>
</template>

<script setup lang="ts">
  import { ref } from 'vue';
  
  const currentYear = ref<number>(new Date().getFullYear());
  const siteIcp = ref(import.meta.env.VITE_FT_ICP);
  const name = ref(import.meta.env.VITE_DESC_NAME);
  const year = ref(import.meta.env.VITE_FT_STARTYEAR);
</script>

<style scoped lang="scss">
  /* Footer样式 */
  .footer {
    position: fixed; /* 修改为 fixed 定位，使其始终位于页面底部 */
    display: flex;
    align-items: center;
    justify-content: center;
    bottom: 0;
    height: 60px;
    width: 100%;
    font-size: 14px;
    color: var(--main-text-color);
    z-index: 1;
  }
  
  a {
    text-decoration: none;
    color: var(--main-text-color);
  }
  
  /* 自适应 */
  @media all and (max-height: 490px) {
    .footer {
      display: none; /* 当页面高度小于 490px 时隐藏 footer */
    }
  }
</style>