<script>
import { DataSet, Network } from 'vis-network/standalone/esm/vis-network'
import spImage from '@/assets/sp.png'

export default {
  name: 'App',
  data() {
    return {
      nodes: new DataSet([
        {
          id: 1,
          label: 'Stephen',
          shape: 'circularImage',
          borderWidth: 3,
          image: spImage,
          shapeProperties: {
            useBorderWithImage: true
          },
          font: {
            color: '#000000'
          }
        },
        { id: 2, label: 'Node 2' },
        { id: 3, label: 'Node 3' },
        { id: 4, label: 'Node 4' },
        { id: 5, label: 'Node 5' }
      ]),
      edges: new DataSet([
        { from: 1, to: 3 },
        { from: 1, to: 2 },
        { from: 2, to: 4 },
        { from: 2, to: 5 }
      ])
    }
  },
  mounted() {
    const container = this.$refs.networkContainer
    const data = {
      nodes: this.nodes,
      edges: this.edges
    }
    const options = {
      nodes: {
        color: {
          border: '#5d90b6',
          background: '#5d90b6'
        },
        font: {
          color: '#ffffff',
          bold: {
            color: '#ffffff',
            vadjust: 0,
            mod: 'bold'
          }
        }
      },
      edges: {
        color: '#7ae7c7',
        width: 2
      }
    }
    new Network(container, data, options)
  }
}
</script>

<template>
  <main ref="networkContainer" class="network-container"></main>
</template>

<style scoped>
/*
  5d90b6
  3f784c
  7ae7c7
  ee6352
  05299e
*/
.network-container {
  --accent: #5d90b6;
  --highlight: #f8f991;
  height: 350px;
  width: 100%;
}
</style>
