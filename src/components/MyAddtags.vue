<template>
  <div>
    <button
      class="btn btn-primary btn-sm"
      v-if="isShow"
      @dblclick="isShow = false"
    >
      +Tag
    </button>
    <input
      v-else
      type="text"
      style="width: 80px"
      v-model="tagname"
      v-focus
      @blur="addTags(tagname)"
      @keydown.enter="addTags"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      isShow: true,
      tagname: ''
    }
  },
  methods: {
    addTags() {
      this.isShow = true
      if (this.tagname !== '') {
        this.$emit('add-tags', this.tagname)
      }
      this.tagname = ''
    }
  },
  directives: {
    focus: {
      inserted(el) {
        el.focus()
      }
    }
  }
}
</script>

<style></style>
