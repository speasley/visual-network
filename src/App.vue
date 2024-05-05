<script>
import { DataSet, Network } from 'vis-network/standalone/esm/vis-network'
import spImage from '@/assets/sp.png'

export default {
  name: 'App',
  data() {
    const colourCategory = '#ee6352'
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
        {
          id: 2,
          label: 'Social Media',
          color: { background: colourCategory, border: colourCategory }
        },
        {
          id: 3,
          label: 'Education',
          color: { background: colourCategory, border: colourCategory }
        },
        {
          id: 4,
          label: 'Communication',
          color: { background: colourCategory, border: colourCategory }
        },
        { id: 5, label: 'Work', color: { background: colourCategory, border: colourCategory } },
        { id: 6, label: 'Posts' },
        { id: 7, label: 'Reddit' },
        { id: 8, label: 'Spotify' },
        { id: 9, label: 'Instagram' },
        { id: 10, label: 'Wikipedia' },
        { id: 11, label: 'Email' },
        { id: 12, label: 'Facebook' },
        { id: 13, label: 'Twitter/X' },
        { id: 14, label: 'YouTube' },
        { id: 15, label: 'Bluesky' },
        {
          id: 16,
          label: 'Entertainment',
          color: { background: colourCategory, border: colourCategory }
        },
        {
          id: 17,
          label: 'Education',
          color: { background: colourCategory, border: colourCategory }
        },
        { id: 18, label: 'Signal' }
      ]),
      edges: new DataSet([
        { from: 1, to: 2 }, // top-level edges
        { from: 1, to: 3 },
        { from: 1, to: 4 },
        { from: 1, to: 5 },
        { from: 6, to: 2 }, // social media
        { from: 7, to: 2 },
        { from: 8, to: 2 },
        { from: 9, to: 2 },
        { from: 12, to: 2 },
        { from: 13, to: 2 },
        { from: 15, to: 2 },
        { from: 1, to: 16 }, // entertainment
        { from: 1, to: 17 }, // education
        { from: 14, to: 16 },
        { from: 14, to: 17 },
        { from: 11, to: 4 },
        { from: 10, to: 16 },
        { from: 10, to: 17 },
        { from: 18, to: 4 }
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
.network-container {
  height: 350px;
  width: 100%;
}
</style>
