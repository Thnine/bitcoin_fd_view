<template>
  <div id="app">
    <fdView ref="fdView" style="width:600px;height:600px" @exportChosenNodes="handleExportChosenNodes"></fdView>
  </div>
</template>

<script>
import fdView from './components/fdView/fdView'
import * as d3 from 'd3'
export default {
  name: 'App',
  components: {
    fdView
  },
  methods:{
    handleExportChosenNodes(ids){//圈选测试
      console.log('ids:',ids)
    }
  },
  mounted(){
    d3.json('static/links1.json',(links)=>{
      d3.json('static/nodes1.json',(nodes)=>{
        this.$refs['fdView'].start(nodes,links)
        // this.$refs['fdView'].setFilter(['id7','id8','id9'])//过滤器测试
        // this.$refs['fdView'].highlightNodes(['id1','id2','id3'])//高亮测试
      })
    })

  },
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
