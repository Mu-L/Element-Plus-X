<script lang='ts' setup>
import type { ThoughtChainItemProps } from 'vue-element-plus-x/types/components/ThoughtChain/types'

const thinkings = ref<ThoughtChainItemProps[]>([{
  id: '1',
  thinkTitle: 'content--收到问题',
  title: 'title--进行搜索文字',
  status: 'success',
  isCanExpand: true,
  isDefaultExpand: false,
  thinkContent: '进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字',
}])

const thinkingItems = ref<ThoughtChainItemProps[]>([
  {
    id: '1',
    thinkTitle: 'content--收到问题',
    title: 'title--进行搜索文字',
    status: 'success',
    isCanExpand: true,
    isDefaultExpand: true,
    thinkContent: 'expandContent--进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字',
  },
  {
    id: '2',
    thinkTitle: 'content--找到问题',
    title: 'title--思考中',
    status: 'loading',
  },
])

setTimeout(() => {
  thinkingItems.value[1] = {
    ...thinkingItems.value[1],
    status: 'success',
  }
  thinkingItems.value.push({
    id: '3',
    thinkTitle: 'content--解决问题 title--被隐藏了  打字动画建议只给最后一个思维链接',
    title: 'title--进行搜索文字',
    hideTitle: true,
    status: 'loading',
    isCanExpand: true,
    isDefaultExpand: true,
    isMarkdown: false,
    typing: {
      step: 4,
      interval: 60,
    },
    thinkContent: 'expandContent--进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字进行搜索文字',
  })
}, 4000)
</script>

<template>
  <div class="component-container">
    <ThoughtChain :thinking-items="thinkings" :line-gradient="true" /> <br>
    <ThoughtChain :thinking-items="thinkingItems" :line-gradient="true" /> <br>
    <ThoughtChain :thinking-items="thinkingItems" @handle-expand="(id:string[]) => console.log(id)">
      <template #customDot="{ item, parentProps }">
        <el-button
          :size="parentProps.dotSize" :type="item.type" :icon="item.dotIcon" :loading="item.isLoading"
          :loading-icon="item.loadingIcon" circle
        />
      </template>
    </ThoughtChain>
  </div>
</template>

<style lang='scss' scoped>
.component-container {
  background-color: white;
  padding: 12px;
  border-radius: 15px;
}
</style>
