<template>
  <div class="q-pa-md">
    <q-carousel animated v-model="slide" control-color="grey-1" arrows infinite autoplay height="400px">
      <q-carousel-slide :name="1" img-src="https://cdn.quasar.dev/img/mountains.jpg" />
      <q-carousel-slide :name="2" img-src="https://cdn.quasar.dev/img/parallax1.jpg" />
      <q-carousel-slide :name="3" img-src="https://cdn.quasar.dev/img/parallax2.jpg" />
      <q-carousel-slide :name="4" img-src="https://cdn.quasar.dev/img/quasar.jpg" />

      <template v-slot:control>

        <q-carousel-control :offset="[-5, 18]" class="q-gutter-xs absolute-center">
          <b class="title">一二三四五六七八九</b>
          <p class="subtitle">仁的本性是</p>
          <p> 這邊明天來做 Input </p>

          <!-- 搜尋框 start-->
          <q-select label="輸入城市/景點" dropdown-icon="fas fa-search-location" bg-color="grey-1" filled :model-value="model"
            use-input hide-selected fill-input input-debounce="500" :options="options" @filter="advFilter"
            @input-value="setModel" style="padding-bottom: 32px" behavior="menu">
            <!-- option start-->
            <template v-slot:option="scope">
              <q-item>
                <q-item-section avatar>
                  <q-icon :name="scope.opt.icon"></q-icon>
                </q-item-section>
              </q-item>
            </template>
            <!-- option end -->

            <!-- no option start-->
            <template v-slot:no-option>
              <q-item>
                <q-item-section class="text-grey">
                  No results
                </q-item-section>
              </q-item>
            </template>
            <!-- no option end-->
          </q-select>
          <!-- 搜尋框 end -->
        </q-carousel-control>
      </template>
    </q-carousel>
  </div>
</template>

<script>
import { ref } from 'vue'
import _ from 'lodash'

const locations = [
  { label: '台北市', icon: 'fas fa-map-marker-alt' },
  { label: '新北市', icon: 'fas fa-map-marker-alt' },
  { label: '台中市', icon: 'fas fa-map-marker-alt' },
  { label: '「網美景點」台中秋紅谷，秋季賞楓勝地', icon: 'fas fa-map-marker-alt', stamp: '台中市' },
  { label: '東京台場「獨角獸鋼彈」強勢來襲！精彩變身演出搶先看', icon: 'fas fa-map-marker-alt', stamp: '東京, 台場', rightTextColor: 'pink-13' }
]

export default {
  setup () {
    const search = ref('')
    const options = ref(locations)
    const model = ref(null)

    const advFilter = (terms, update, abort) => {
      update(() => {
        const result = _.filter(locations, context => {
          return context.label.match(terms)
        })
        options.value = result
      })
    }

    const setModel = (val) => { model.value = val }

    return {
      slide: ref(1),
      options,
      search,
      model,
      advFilter,
      setModel
    }
  }
}
</script>

<style lang="scss">
.q-carousel__control {
  text-align: center;

  @media (min-width: 768px) {
    .title {
      font-size: 48px;
    }

    .subtitle {
      font-size: 24px;
    }
  }

  @media (max-width: 768px) {
    .title {
      font-size: 24px;
    }

    .subtitle {
      font-size: 16px;
    }
  }
}

.q_item {
  width: 100%;
}
</style>