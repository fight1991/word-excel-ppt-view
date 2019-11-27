<template>
  <div class='doc-view'  v-loading="loading">
    <iframe @load='docLoad' :id='id' width='100%' :src="'https://view.officeapps.live.com/op/view.aspx?src='+url" height="100%" sandbox="allow-forms allow-popups allow-scripts allow-same-origin allow-top-navigation allow-modals" frameborder=0 scrolling=auto></iframe>
  </div>
</template>

<script>
export default {
  name: 'doc-view',
  props: ['url'],
  data () {
    return {
      loading: true,
      id: new Date().getTime()
    }
  },
  mounted () {
    this.loading = true
  },
  methods: {
    // 遮罩处理
    docLoad () {
      this.loading = false
    }
  },
  beforeDestroy () {}
}
</script>

<style lang="less" scoped>
.doc-view{
  height: 100%;
  box-sizing: border-box;
  overflow: hidden;
  iframe{
    position: relative;
    box-sizing: border-box;
  }
}
.autoH{
  height: auto;
}
.defultH{
  height: 200px;
}
</style>
