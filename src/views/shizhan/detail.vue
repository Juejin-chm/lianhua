<template>
  <div>
    <div class="title">人大代表联系群众活动室(站)-{{ route.query.street }}</div>
    <div class="item-wrapper">
      <template v-for="(item, index) in resList">
        <div class="item pointer" @click="viewDetail(item)" :class="[item.className]">
          <img :src="item.imgUrl">
          <div class="item-text">{{ item.title }}</div>
        </div>
      </template>
    </div>
  </div>
</template>
<script setup>
import { reactive } from 'vue';
import { useRouter, useRoute } from 'vue-router'

// import img1 from '@/assets/img/touxiang.png'
import img2 from '@/assets/img/touxiang2.png'
import img3 from '@/assets/img/touxiang3.png'

const router = useRouter()
const route = useRoute()

const data = reactive({
  list: [
    // { title: '“莲”心助力--人大代表风采', id: 1, imgUrl: img1, className: 'item-1' },
    { title: '各社区人大代表联系群众活动站', id: 2, imgUrl: img2, className: 'item-2' },
    { title: '代表档嘉莲街道人大代表联系群众活动室案', id: 3, imgUrl: img3, className: 'item-3' }
  ]
})
const resList = computed(() => {
  if (route.query.id == 0) {
    return data.list.slice(1)
  } else {
    return data.list
  }
})
function viewDetail(item) {
  router.push({ name: 'shizhanDetailInner', params: { name: item.id }, query: { ...route.query, streetTitle: item.title } })
}
</script>
<style lang="scss" scoped>
.title {
  font-size: 44px;
  color: #111111;
  text-align: center;
  margin-top: 131px;
  margin-bottom: 105px;
}
.item-wrapper {
  display: flex;
  gap: 68px;
  justify-content: center;
}
.item {
  width: 500px;
  height: 320px;
  background: linear-gradient(-135deg, #41D0F3, #33BAF9);
  position: relative;
  padding-top: 1px;
  // &:nth-child(2) {
  //   background: linear-gradient(-135deg, #3DCDBD, #1FCAA3);
  // }
  // &:nth-child(3) {
  //   background: linear-gradient(-135deg, #70B5FF, #4F84E1);
  // }
  &-2 {
    background: linear-gradient(-135deg, #3DCDBD, #1FCAA3);

  }
  &-3 {
    background: linear-gradient(-135deg, #70B5FF, #4F84E1);
  }
  img {
    width: 154px;
    height: 154px;
    display: block;
    margin: 53px auto 32px;
  }
  &-text {
    width: 100%;
    text-align: center;
    font-size: 28px;
    color: white;
    font-weight: bold;
  }
}
</style>