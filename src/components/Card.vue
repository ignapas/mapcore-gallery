<template>
  <el-card :body-style="{ padding: '0px' }" class="card">
    <img :src="data.thumbnail" alt="thumbnail missing" :style="`max-width: ${width}rem; height: ${imageHeight}rem`" />
    <div class="image-overlay">
      <div
        class="triangle-right-corner"
        :style="`border-left-width: ${triangleHeight * 1.2}rem; border-top-width: ${triangleHeight}rem;`"
        @click="$emit('view')"
      ></div>
      <el-tooltip class="item" :content="`View ${data.type}`" placement="left">
        <img
          class="triangle-icon"
          :style="`height: ${triangleHeight * 0.25}rem;top: ${triangleHeight * 0.15}rem;right: ${triangleHeight * 0.15}rem`"
          :src="typeIcon"
          @click="$emit('view')"
        />
      </el-tooltip>
    </div>
    <div v-if="showCardDetails" class="details" :style="`margin: ${marginDetails}rem`">
      <p>
        <b>{{ data.type }}</b
        ><br />{{ data.title }}
      </p>
      <el-button @click.prevent="$emit('view')">View {{ data.type }}</el-button>
    </div>
  </el-card>
</template>

<script>
export default {
  name: 'GalleryCard',
  props: {
    data: {
      type: Object,
      required: true,
    },
    width: {
      type: Number,
      default: 3,
    },
    height: {
      type: Number,
      default: 3,
    },
    showCardDetails: {
      type: Boolean,
    },
  },
  data() {
    return {
      triangleSize: 4,
    }
  },
  computed: {
    imageHeight() {
      return this.showCardDetails ? this.height * 0.525 : this.height
    },
    triangleHeight() {
      return this.height * 0.237
    },
    marginDetails() {
      return this.height * 0.076
    },
    typeIcon() {
      if (this.data.type == '3D Image') {
        return require('../assets/3d_image_icon.svg')
      } else if (this.data.type == '3D Scaffold') {
        return require('../assets/scaffold_image_icon.svg')
      }
      return require('../assets/2d_image_icon.svg')
    },
  },
}
</script>

<style scoped>
.card.old {
  box-shadow: 0 0.125rem 0.75rem 0 rgba(0, 0, 0, 0.25);
  border: solid 0.0625rem var(--pale-grey);
  background-color: #ffffff;
  display: inline-block;
  position: relative;
}

.card {
  position: relative;
}
.details {
  text-align: left;
}

p.bold {
  font-weight: bold;
}

.image-overlay {
  position: absolute;
  top: 0;
  right: 0;
}

.triangle-icon {
  position: absolute;
}

.triangle-right-corner {
  width: 0;
  height: 0;
  border-left: solid transparent;
  border-top: solid #8300bf;
}
</style>
