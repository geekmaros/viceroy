<template>
  <section class="tv">
    <HorizontalTreeView :node="root" class="node-wrapper"></HorizontalTreeView>
  </section>
</template>

<script>
import HorizontalTreeView from "../components/HorizontalTreeView";
import { v4 as uuidv4 } from "uuid";
export default {
  name: "TreeView",
  components: { HorizontalTreeView },
  data() {
    return {
      root: {
        NodeID: uuidv4(),
        nodeLabel: "Viceroy",
        children: [
          {
            NodeID: uuidv4(),
            nodeLabel: "irena",
            children: [
              {
                NodeID: uuidv4(),
                nodeLabel: "fred",
              },
              {
                NodeID: uuidv4(),
                nodeLabel: "Eva",
              },
            ],
          },
          {
            NodeID: uuidv4(),
            nodeLabel: "mayank",
            children: [
              {
                NodeID: uuidv4(),
                nodeLabel: "abdul",

                children: [
                  {
                    NodeID: uuidv4(),
                    nodeLabel: "Michael",
                  },
                  {
                    NodeID: uuidv4(),
                    nodeLabel: "Lovelace",
                  },
                ],
              },
              {
                NodeID: uuidv4(),
                nodeLabel: "steve",
              },
            ],
          },
        ],
      },
    };
  },
};
</script>

<style lang="scss">
.tv {
  margin: 10rem 5rem 0 10rem;
  width: 100%;
  transition: all 0.09s ease-in-out;

  .parent {
  }
  .child-node {
    max-width: max-content;
    display: flex;
    margin: 20px;
    transition: all 0.09s ease-in-out;
  }
  span {
    font-size: 15px;
  }
  .node-wrapper {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    transition: all 0.09s ease-in-out;
    &::before {
      content: "";
      width: 20px;
      height: 1px;
      border: 1px solid #777;
    }
  }
  .main {
    transition: all 0.09s ease-in-out;
    background-color: white;
    height: max-content;
    width: 200px;
    padding: 10px 15px;
    text-align: center;
    border-radius: 3px;
    box-shadow: 0 1px 5px #777777;
    font-size: 20px;
    position: relative;
  }
  .children-wrapper {
    display: table-cell;
    padding-top: 0;
    //padding-left: 20px;
    margin-left: 10px;
  }
  .node-btn {
    margin-right: -20px;
    position: absolute;
    right: 0;
    transform: scale(1.4);
    font-weight: bold;
    color: #777777;
  }
}
</style>
