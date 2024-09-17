<template>
  <log-viewer class="auto-scroll" :log="log" :auto-scroll="false" />
</template>
<script>
  const get = url => new Promise((resolve, reject)=>{
    const xhr = new XMLHttpRequest()
    xhr.open("GET",url)
    xhr.send()
    xhr.onload = data => resolve(data.target.responseText)
  })
  export default{
    data(){
      return {
        log: '',
        autoes: [true, false]
      }
    },
    mounted(){
      this.getTravisLog()
    },
    methods:{
      getTravisLog(){
        const travisUrl = 'http://mockapi.eolinker.com/IeZWjzy87c204a1f7030b2a17b00f3776ce0a07a5030a1b/log-viewer' // you can edit other travisUrl.
        get(travisUrl).then((text)=>{
          this.log = text
        })
      },
    }
  }
</script>
<style>
.auto-scroll{
  margin-bottom: 8px;
}
</style>