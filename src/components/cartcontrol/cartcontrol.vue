<template>
  <div class="cartcontrol">
    <transition name="move">
      <div class="cart-decrease" v-show="food.count>0" @click.stop.prevent="decreaseCart">
      </div>
    </transition>
    <div class="cart-count" v-show="food.count>0">{{ food.count }}</div>
    <div class="cart-add" @click.stop.prevent="addCart"></div>
  </div>
</template>

<script type="text/ecmascript-6">
import Vue from 'vue';

export default {
  props: {
    food: {
      type: Object
    }
  },
  methods: {
    addCart(event) {
      if (!event._constructed) {
        return;
      }
      if (!this.food.count) {
        Vue.set(this.food, 'count', 1);
        // this.food.count = 1;
      } else {
        this.food.count++;
      }
      this.$emit('add', event.target);
    },
    decreaseCart(event) {
      if (!event._constructed) {
        return;
      }
      if (this.food.count) {
        this.food.count--;
      }
    }
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
.cartcontrol
  font-size 0
  .cart-decrease, .cart-add
    display inline-block
    width 25px
    height 25px
    line-height 25px
    background-repeat no-repeat
  .cart-decrease
    background-image url("cartcontrol_increase.png")
    &.move-enter-active
      animation-name fold-in
      animation-duration .5s
    &.move-leave-active
      animation-name fold-out
      animation-duration .5s
    @keyframes fold-in {
      0% {
        transform translate3d(100%, 0, 0)
        opacity 0
        transform rotate(0)
      }
      50% {
        transform translate3d(50%, 0, 0)
        opacity 0.5
        transform rotate(90deg)
      }
      100% {
        transform translate3d(0, 0, 0)
        opacity 1
        transform rotate(180deg)
      }
    }
    @keyframes fold-out {
      0% {
        transform translate3d(0, 0, 0)
        opacity 1
        transform rotate(180deg)
      }
      50% {
        transform translate3d(50%, 0, 0)
        opacity 0.5
        transform rotate(90deg)
      }
      100% {
        transform translate3d(100%, 0, 0)
        opacity 0
        transform rotate(0)
      }
    }
  .cart-count
    display inline-block
    vertical-align top
    width 12px
    margin 0 5px
    line-height 24px
    text-align center
    font-size 12px
    color rgb(147, 153, 159)
  .cart-add
    background-image url("cartcontrol_add.png")
</style>
