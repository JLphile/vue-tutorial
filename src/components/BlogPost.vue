<template>
  <div>
    <h1>
      <a :href="link" @click.prevent="$emit('titleClick', title)">{{
        title
      }}</a>
    </h1>
    <article>
      <div>
        {{ content.slice(0, 100) }}
      </div>
      <p>阅读量:{{ viewCount }}</p>
      <footer v-if="content.length > 100">
        <button>阅读原文</button>
      </footer>
    </article>
    <!-- 用来接收父组件传递的模板代码块 -->
    <slot></slot>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
// 接收父组件数据
defineProps(["title", "content", "link"]);

// 定义触发事件提供给父组件处理
defineEmits(["titleClick"]);

const viewCount = ref(0);

onMounted(() => {
  setTimeout(() => {
    viewCount.value = 1000000;
  }, 1000);
});
</script>

<style scoped></style>
