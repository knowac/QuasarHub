<template>
    <div class="layout-view">
        <div class="layout-padding">
            <q-infinite-scroll :handler="loadMore" inline class="infinite-scroll">
                <div class="card" v-for="image in images">
                    <q-parallax v-bind:src="image.img" :width="150" :height="100">
                        <div slot="loading">Loading...</div>
                    </q-parallax>
                    <div class="card-content" >
                        Card Content
                    </div>
                </div>
                <spinner slot="message" name="dots" :size="40"></spinner>
            </q-infinite-scroll>
        </div>
    </div>
</template>

<script>
let arr = []
const el = {
  img: 'https://paoc.org/images/default-source/mission-canada-images/Canada/yellowknife-nwt.jpg'
}
const pupulateArr = () => {
  arr = []
  for (let x = 0; x < 20; x++) {
    arr.push(el)
  }
}
pupulateArr()

export default {
  data () {
    return {
      images: arr
    }
  },
  destroyed () {
    this.$children[0].reset()
    pupulateArr()
  },
  methods: {
    loadMore (num, done) {
      const count = (num * 20) + 20
      const limit = count < 1000 ? count : 1000
      for (let x = num * 20; x < limit; x++) {
        arr.push(el)
      }
      done()
    }
  }
}
</script>

<style>
.infinite-scroll {
    text-align: center;
    height: 720px;
    overflow: auto;
}
.card {
    text-align: center;
    display: inline-block;
    width: 150px;
    height: 150px;
    padding: 5px 5px 5px 5px;
}
</style>
