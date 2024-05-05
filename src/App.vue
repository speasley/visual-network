<script>
import { DataSet, Network } from 'vis-network/standalone/esm/vis-network'
import spImage from '@/assets/sp.png'

export default {
  name: 'App',
  data() {
    const colourCategory = '#ee6352'
    const colourCategoryOutline = '#eb4833'
    const sizeCategory = 18
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
          label: 'Social Media'.toUpperCase(),
          color: { background: colourCategory, border: colourCategoryOutline },
          font: { size: sizeCategory }
        },
        {
          id: 3,
          label: 'Education'.toUpperCase(),
          color: { background: colourCategory, border: colourCategoryOutline },
          font: { size: sizeCategory }
        },
        {
          id: 4,
          label: 'Communication'.toUpperCase(),
          color: { background: colourCategory, border: colourCategoryOutline },
          font: { size: sizeCategory }
        },
        {
          id: 5,
          label: 'Work'.toUpperCase(),
          color: { background: colourCategory, border: colourCategoryOutline },
          font: { size: sizeCategory }
        },
        { id: 6, label: 'Posts.cv' },
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
          label: 'Entertainment'.toUpperCase(),
          color: { background: colourCategory, border: colourCategoryOutline },
          font: { size: sizeCategory }
        },
        { id: 17, label: 'Discord' },
        { id: 18, label: 'Signal' },
        { id: 19, label: 'StackOverflow' },
        { id: 20, label: 'Royal Roads University' },
        { id: 21, label: 'GitHub' },
        { id: 22, label: 'Coursera' },
        { id: 23, label: 'Udemy' },
        { id: 24, label: 'Read.cv' },
        { id: 25, label: 'LinkedIn' },
        { id: 26, label: 'MS Teams' },
        { id: 27, label: 'SAIT' }
      ]),
      edges: new DataSet([
        { from: 1, to: 2 }, // social media
        { from: 1, to: 3 }, // education
        { from: 1, to: 4 }, // communication
        { from: 1, to: 5 }, // work
        { from: 1, to: 16 }, // entertainment
        { from: 6, to: 2 }, // posts
        { from: 7, to: 2 }, // reddit
        { from: 7, to: 16 },
        { from: 8, to: 2 }, // spotify
        { from: 9, to: 2 }, // instagram
        { from: 9, to: 16 }, // instagram
        { from: 10, to: 16 }, // wikipedia
        { from: 10, to: 3 },
        { from: 11, to: 4 }, // email
        { from: 12, to: 2 }, // facebook
        { from: 12, to: 4 },
        { from: 13, to: 2 }, // twitter
        { from: 15, to: 2 }, // bluesky
        { from: 14, to: 16 }, // YouTube
        { from: 14, to: 3 },
        { from: 17, to: 2 }, // discord
        { from: 17, to: 3 },
        { from: 17, to: 4 },
        { from: 17, to: 16 },
        { from: 18, to: 4 }, // signal
        { from: 19, to: 5 }, // StackOverflow
        { from: 19, to: 3 },
        { from: 20, to: 3 }, // RRU
        { from: 21, to: 5 }, // GitHub
        { from: 22, to: 3 }, // Coursera
        { from: 23, to: 3 }, // Udemy
        { from: 24, to: 2 }, // Read.cv
        { from: 24, to: 4 },
        { from: 24, to: 5 },
        { from: 25, to: 2 }, // LinkedIn
        { from: 25, to: 4 },
        { from: 25, to: 5 },
        { from: 26, to: 5 }, // Teams
        { from: 27, to: 5 } // SAIT
        { from: 27, to: 3 }
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
        color: {
          color: '#eaeaea',
          highlight: '#7ae7c7'
        },
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
  height: 500px;
  width: 100%;
}
</style>
