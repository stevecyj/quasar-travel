<template>
  <div class="q-pa-md">
    <q-carousel animated v-model="slide" control-color="grey-1" arrows infinite autoplay height="400px">
      <q-carousel-slide :name="1" img-src="https://cdn.quasar.dev/img/mountains.jpg" />
      <q-carousel-slide :name="2" img-src="https://cdn.quasar.dev/img/parallax1.jpg" />
      <q-carousel-slide :name="3" img-src="https://cdn.quasar.dev/img/parallax2.jpg" />
      <q-carousel-slide :name="4" img-src="https://cdn.quasar.dev/img/quasar.jpg" />

      <template v-slot:control>

        <q-carousel-control position="center" :offset="[0, 18]" class="q-gutter-xs">
          <b class="title">一二三四五六七</b>
          <p class="subtitle">仁的本性是</p>
          <p> 這邊明天來做 Input </p>
        </q-carousel-control>
      </template>
    </q-carousel>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      slide: ref(1)
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
</style>