<template>
	<div class="weui_cell" v-if="!isLink">
    <div class="weui_cell_hd">
      <slot name="icon"></slot>
    </div>
  	<div class="weui_cell_bd" :class="{'weui_cell_primary':primary==='title'}">
    	<p>
        {{title}}
        <slot name="after-title"></slot>
      </p>
    	<inline-desc>{{inlineDesc}}</inline-desc>
  	</div>
  	<div class="weui_cell_ft" :class="{'weui_cell_primary':primary==='content'}">
      {{{value}}}
      <slot name="value"></slot>
    </div>
	</div>
	<a class="weui_cell" :href="link" v-if="isLink" v-link="link">
    <div class="weui_cell_hd">
      <slot name="icon"></slot>
    </div>
    <div class="weui_cell_bd" :class="{'weui_cell_primary':primary==='title'}">
      <p>{{title}}</p>
      <inline-desc v-if="inlineDesc">{{inlineDesc}}</inline-desc>
    </div>
    <div class="weui_cell_ft with_arrow" :class="{'weui_cell_primary':primary==='content'}">
      {{{value}}}
      <slot name="value"></slot>
    </div>
  </a>
</template>

<script>
import InlineDesc from '../inline-desc/'

export default {
  created () {
    if (this.link) {
      this.isLink = true
    }
  },
  components: {
    InlineDesc
  },
  props: {
    title: {
      type: String
    },
    value: {
      type: String
    },
    link: {
      type: String
    },
    inlineDesc: {
      type: String
    },
    primary: {
      type: String,
      default: 'title'
    }
  },
  data () {
    return {
      isLink: false
    }
  }
}
</script>

<style>
</style>
