<template>
  <section
    class="node-wrapper"
    draggable="true"
    @dragover="dropNode"
    @dragover.prevent
  >
    <!--    div below indicates each individual elements-->
    <div
      @click="expanded = !expanded"
      :style="{ 'margin-left': depth * 20 + 'px' }"
      class="main"
      draggable="true"
      @dragstart="dragNode"
      @dragover.stop
    >
      <span class="node-btn" v-show="node.children">{{
        expanded ? "&#8854;" : "&#8853;"
      }}</span>
      {{ node.name }}
      <span v-if="node.role" class="sm-text">({{ node.role }})</span>
    </div>
    <div v-if="expanded" class="children-wrapper">
      <HorizontalTreeView
        v-for="child in node.children"
        :key="child.id"
        :node="child"
        :depth="depth + 1"
        class="child"
      />
    </div>
  </section>
</template>

<script>
export default {
  name: "HorizontalTreeView",
  data() {
    return {
      expanded: false,
    };
  },
  props: {
    node: Object,
    depth: {
      type: Number,
      default: 0,
    },
    draggable: {
      type: Boolean,
      default: true,
    },
  },
  components: {},
  methods: {
    dropNode: (e) => {
      console.log(e);
      // const node_id = e.dataTransfer.getData("node_id");
      // const node = document.getElementById(node_id);
      // node.style.display = "block";
      // e.target.appendChild(node);
    },
    dragNode: (e) => {
      const { target } = e;
      e.dataTransfer.setData("node_id", target.id);
      // console.log(e + "DRAG" + target.id);
      // setTimeout(() => {
      //   target.style.display = "none";
      // }, 0);
    },
  },
};
</script>

<style scoped lang="scss">
* {
  transition: all 0.09s ease-in-out;
}
</style>
