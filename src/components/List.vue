<script setup lang="ts">
const router = useRouter()
const data = ref([])
const toDdetail = (id: number) => {
  if (id)
    router.push(`${window.location.pathname}${encodeURIComponent(id)}`)
}
function getFile() {
  fetch('data.json').then(res => res.json()).then(res => data.value = res.data)
}
getFile()
</script>

<template>
  <div style="height:calc(100vh - 2.5rem);overflow: auto;">
    <div
      class="common" style="max-width: 18.75rem;
    margin-left: auto;
    margin-right: auto;"
    >
      <img
        style="
    width: 100%;
    height: 10rem;" data-src="images/1662536511070.jpg" class="headerPic" title="Ways to Save on Currency Exchanges"
        src="https://reidkblackman.com/images/1662536511070.jpg"
      >
    </div>
    <div
      class="common" style="max-width: 18.75rem;
    margin-left: auto;
    margin-right: auto;"
    >
      <i
        class="titles weight" style="padding: 0.3rem 0;
    display: block;
    text-align: center;
    color: #fff;
    background: linear-gradient(270deg, #CC8466 0%, #5A3023 100%);
    margin-top: 0.5rem;"
      >Headlines Today</i>
    </div>
    <ul
      style="    max-width: 18.75rem;
    margin-left: auto;
    margin-right: auto;"
    >
      <li
        v-for="item in data" :key="item.id" class="everyGoods" style="padding: 0.4rem;
    border-radius: 0.4rem;
    background-color: #fff;
    margin-top: 0.6rem;" @click="toDdetail(item.id)"
      >
        <img :src="`http://47.104.212.164:3000/${item.picture}`" style="width: 100%;">
        <div class="namesAmoney weight flex">
          <i
            class="lineFeed_2" style="    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;    color: #5A3023;
    font-size: .8rem;
"
          >{{ item.title }}</i>
        </div>
        <i
          class="goodContent lineFeed_3" style="overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;font-size: .6rem;
}"
        >{{ item.description }}</i>
      </li>
    </ul>
    <Footer />
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
