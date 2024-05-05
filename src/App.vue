<script>
import { DataSet, Network } from 'vis-network/standalone/esm/vis-network'

export default {
  name: 'App',
  data() {
    return {
      nodes: new DataSet([]),
      edges: new DataSet([])
    }
  },
  mounted() {
    const container = this.$refs.networkContainer
    const data = {
      nodes: this.nodes,
      edges: this.edges
    }
    new Network(container, data, {})
  }
}
</script>

<template>
  <main ref="networkContainer" class="network-container"></main>
</template>

<style scoped>
.network-container {
  height: 350px;
  width: 100%;
}
</style>
