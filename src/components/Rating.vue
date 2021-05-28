<template>
  <div class="rating">
    <ul class="list">
      <li @click="rate(star)" v-for="(star,index) in maxStars" :class="{ 'active': star <= stars }" :key="index" class="star">
      <i :class="star <= stars ? 'fas fa-star' : 'far fa-star'"></i> 
      </li>
    </ul>
<!--     <div v-if="hasCounter" class="info counter">
      <span class="score-rating">{{ stars }}</span>
      <span class="divider">/</span>
      <span class="score-max">{{ maxStars }}</span>
    </div> -->
  </div>
</template>
<script>
export default {
  name: 'Rating',
  props: ['grade', 'maxStars'],
  data() {
    return {
      stars: this.grade
    }
  },
  methods: {
    rate(star) {
      if (star <= this.maxStars && star >= 0) {
        this.stars = this.stars === star ? star - 1 : star
      }
    }
  },
}
</script>


<style scoped lang="scss">
  @import '../assets/style/star.scss'
</style>