<template>
  <section
    :id="node.NodeID"
    class="node-wrapper"
    draggable="true"
    @dragover="dropNode"
    @dragover.prevent
    @dragstart="dragNode"
    @dragover.stop
  >
    <!--    div below indicates each individual elements-->
    <!--          :style="{ 'margin-left': depth * 20 + 'px' }"

     draggable="true"
      @dragstart="dragNode"
      @dragover.stop

      draggable="true"
      @dragstart="dragNode"
      @dragover.stop
    -->
    <div @click="expanded = !expanded" class="main">
      <span class="node-btn" v-show="node.children">{{
        expanded ? "&#8854;" : "&#8853;"
      }}</span>
      {{ node.nodeLabel }}
      <span v-if="node.role" class="sm-text">({{ node.role }})</span>
    </div>
    <div class="children-wrapper">
      <HorizontalTreeView
        v-show="expanded"
        v-for="child in node.children"
        :key="child.NodeID"
        :node="child"
        :depth="depth + 1"
        class="child-node"
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
      const node_id = e.dataTransfer.getData("text");
      const node = document.getElementById(node_id);
      console.log(node);
      // node.style.display = "block";
      // e.target.appendChild(node);
    },
    dragNode: (e) => {
      const { target } = e;
      console.log("Target ID" + target.id);
      e.dataTransfer.setData("text/plain", target.id);
      console.log(e.dataTransfer);

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
