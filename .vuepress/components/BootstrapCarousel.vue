<template>
  <div :id="id" class="carousel slide" data-ride="carousel">
  <ol class="carousel-indicators">
    <li v-for="item, index in items" :data-target="'#' + id" :data-slide-to="index" :class="{active: index===0}"></li>
  </ol>
  <div class="carousel-inner">
    <div v-for="item, index in items" class="carousel-item" :class="{active: index===0}">
      <img class="d-block w-100" :src="item.img" alt="First slide">
    </div>
  </div>
  <a class="carousel-control-prev" :href="'#' + id" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" :href="'#' + id" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
  </a>
</div>
</template>

<script>
export default {
  props: {
    items: Array,
    indicators: {
      type: Boolean,
      default: true
    },
    controlPrevNext: {
      type: Boolean,
      default: true
    },
  },
  computed: {
    id () {
      return 'carousel-' + this._uid
    }
  }
}
</script>