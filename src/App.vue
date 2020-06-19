<template>
  <div id="myDiagramDiv"></div>
</template>

<script>
import go from "gojs";

export default {
  name: "Dijagram",
  methods: {
    init: function() {
      var $ = go.GraphObject.make;
      var myDiagram = $(go.Diagram, "myDiagramDiv");
      var nodeDataArray = [{ key: "Alpha", color: 'lime' }, { key: "Beta", color: 'cyan' }];
      var linkDataArray = [{ to: "Beta", from: "Alpha" }];
      myDiagram.model = new go.GraphLinksModel(nodeDataArray, linkDataArray);
      myDiagram.nodeTemplate = $(
        go.Node,
        "Auto",
        $(go.Shape, "RoundedRectangle", { fill: "white" }),
        $(go.TextBlock, "text")
      );
    },
  },
  mounted: function() {
    this.init();
  },
};
</script>

<style>
#myDiagramDiv {
  width: 500px;
  height: 500px;
  border: 1px solid black;
}
</style>
