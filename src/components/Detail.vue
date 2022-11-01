<script setup lang="ts">
const props = defineProps<{ id: number }>()

const user = useUserStore()
const name = $ref(user.savedName)
const router = useRouter()
const data = ref([])
const toDdetail = (id: number) => {
  if (name)
    router.push(`${window.location.pathname}/${encodeURIComponent(id)}`)
}

function getFile() {
  fetch('data.json').then(res => res.json()).then(res => data.value = res.data.find(item => item.id == props.id))
}
getFile()
</script>

<template>
  <div style="height:calc(100vh - 2.5rem);overflow: auto;">
    <div
      class="details" style="max-width: 18.75rem;
    margin-left: auto;
    margin-right: auto;"
    >
      <div class="top">
        <h1
          style="    margin: 0.5rem 0;
    padding: 0.8rem;
    box-sizing: border-box;
    font-size: 0.95rem;
    line-height: 1.3rem;"
        >
          {{ data.title }}
        </h1>

        <p
          class="name" style="    padding: 0.8rem;
    box-sizing: border-box;
    margin-top: 0.5rem;
    font-size: 0.6rem;"
        >
          {{ data.user_name }}
        </p>
        <p
          class="time" style="    padding: 0.8rem;
    box-sizing: border-box;
    margin-top: 0.2rem;
    font-size: .6rem;
}"
        >
          {{ data.time }}
        </p>
        <div
          class="img" style="display:none;padding: 0.8rem;
    box-sizing: border-box;
    width: 100%;"
        >
          <img data-src="images/1666151333080.jpg" alt="" src="images/1666151333080.jpg">
        </div>
      </div>
      <div
        class="center" style="    width: 100%;
    padding: 0.8rem;
    box-sizing: border-box;
    background-color: #f8f8f8;
    box-shadow: 0 3px 5px #f0f0f0;
    line-height: 1.2rem;
    font-size: .65rem;" v-html="data.content"
      />
    </div>
    <Footer />
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
