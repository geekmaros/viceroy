<template>
  <section class="tv">
    <HorizontalTreeView
      :node="root"
      :draggable="true"
      class="node-wrapper"
    ></HorizontalTreeView>
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
        id: uuidv4(),
        name: "Viceroy",
        children: [
          {
            id: uuidv4(),
            name: "irena",
            role: "Human Resource",
            children: [
              {
                id: uuidv4(),
                name: "fred",
                role: "Marketing Intern",
              },
              {
                id: uuidv4(),
                name: "Eva",
                role: "Ads Manager",
              },
            ],
          },
          {
            id: uuidv4(),
            name: "mayank",
            role: "Tech Lead",
            children: [
              {
                id: uuidv4(),
                name: "abdul",
                role: "Frontend Developer",
                children: [
                  {
                    id: uuidv4(),
                    name: "Michael",
                    role: "Frontend Intern I",
                  },
                  {
                    id: uuidv4(),
                    name: "Lovelace",
                    role: "Frontend Intern  II",
                  },
                ],
              },
              {
                id: uuidv4(),
                name: "steve",
                role: "Backend Developer",
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
  margin: 10rem 0 0 10rem;
  width: 100%;

  transition: all 0.09s ease-in-out;

  .parent {
  }
  .child {
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
    transform: scale(1.6);
    font-weight: bold;
    color: #777777;
  }
}
</style>
