<template>
  <div class="header" @click="showDetail">
    <div class="content-wrapper">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar">
      </div>

      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="description">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
        <div v-if="seller.supports" class="support">
          <support-ico :size="1" :type="seller.supports[0].type"></support-ico>
          <span class="text">{{seller.supports[0].description}}</span>
        </div>
      </div>
      <div v-if="seller.supports" class="support-count">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
import SupportIco from 'components/support-ico/support-ico'
export default {
  name: 'v-header',
  props: {
    seller: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  methods: {
    showDetail () {
      this.headerDetailComp = this.headerDetailComp || this.$createHeaderDetail({
        $props: {
          seller: 'seller'
        }
      })
      this.headerDetailComp.show()
    }
  },
  components: {
    SupportIco
  }
}
</script>
