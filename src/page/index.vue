<template>
  <div>
    <Header/>
    <div class="img_test">
        <img src="static/image/txdsr.png" alt="秦假仙">
    </div>
    <div class="article_list">
      <ul>
        <li v-for="i in list" :key="i.id">
          <!-- <time v-text="i.create_at"></time> -->
          <time v-text="$utils.goodTime(i.create_at)"></time>
          <router-link :to="'/content/' + i.id">
            {{ i.title }}
          </router-link>
        </li>
      </ul>
    </div>
    <Footer/>
  </div>
</template>

<script>
import Header from '../components/header'
import Footer from '../components/footer'
export default {
  components: {Header, Footer},
  data () {
    return {
      list: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topics', null, r => {
        this.list = r.data
        // console.log(r.data)
      })
    }
  }
}
</script>
