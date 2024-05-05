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
          image: spImage,
          shapeProperties: {
            useBorderWithImage: false
          },
          font: {
            background: '#ffffff',
            color: '#000000'
          },
          chosen: {
            node: function (values, id, selected, hovering) {
              values.borderColor = selected ? '#7ae7c7' : '#2b7ce9'
              values.borderWidth = selected ? 6 : 3
            }
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
    new Network(container, data, {
      nodes: {
        borderWidth: 3,
        color: {
          border: '#5d90b6',
          background: '#5d90b6'
        },
        font: {
          color: '#ffffff'
        },
        chosen: {
          node: function (values, id, selected, hovering) {
            values.borderColor = selected ? '#7ae7c7' : '#2b7ce9'
          }
        }
      },
      edges: {
        color: '#7ae7c7',
        width: 2
      }
    })
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
