<template>
  <div id="app" >
    <div class="styleEditor">
      <pre>
       {{ code }}        
      </pre>
    </div>
    <div v-html="styleCode">
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      // 输出到页面上显示的  
      code: ``,
      // 最终代码
      finalCode: `
        body {
          background: red;
        }
      `,
      // 样式代码
      styleCode: ''
    }
  },
  created: function () {
    var n = 0
    setInterval(()=> {
      this.code= this.finalCode.substring(0, n)
      n += 1
    }, 100)
  },
  computed: {
    styleCode: function () {
      return '<style>' + this.code + '</style>'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
