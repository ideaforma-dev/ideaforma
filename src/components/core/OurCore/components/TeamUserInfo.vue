<template>
  <v-card
    flat
    v-bind="cardProps"
    class="smooth-corners"
    style="overflow: hidden"
  >
    <!-- :style="!emphasize ? null : {
      'background-color': `${color}14`
    }" -->
    <v-card-title
      primary
      class="title justify-center"
    >
      <v-img
        :style="imgStyle"
        :src="`${teamPath}${src}`"
        class="speed-3 a-from-bottom"
        v-animate.30="{ above: true }"
        style="filter: grayscale(1)"
      />
    </v-card-title>

    <v-card-text
      v-animate="{ above: true }"
      class="px-0 pt-2 speed-3 a-from-bottom"
    >
      <div
        v-html="name"
        class="text-uppercase primary--text mb-2"
        :class="{
          title: !emphasize,
          'font-weight-bold display-1': emphasize
        }"
      />
      <!-- :style="!emphasize ? null : {
          'font-size': '28px !important'
        }" -->
      <div class="px-3">
        <div
          v-if="title"
          v-text="title"
          class="mt-1 body-1 grey--text text--darken-1"
        />

        <div
          v-if="description"
          v-html="description"
          class="text-xs-justify body-2 pt-3"
        />
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
import { colors } from '@/utils'
import { teamPath } from '@/utils/path'

export default {
  name: 'team-user-info',
  props: {
    name: {
      type: String,
      required: true
    },
    title: {
      type: String,
      default: '',
      required: false
    },
    description: {
      type: String,
      default: null,
      required: false
    },
    src: {
      type: String,
      required: true
    },
    emphasize: {
      type: Boolean,
      default: false,
      required: false
    },
    imgStyle: {
      type: [String, Object],
      default: null,
      required: false
    }
  },

  computed: {
    color: () => colors[2],
    teamPath: () => teamPath,

    // just leave this here
    cardProps() {
      return !this.emphasize ? null : {
        style: {
          // border: `1px solid ${this.color}`
        }
      }
    }
  }
}
</script>
