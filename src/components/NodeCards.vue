<template>
  <div class="node-list" :class="{'node-list_general' : init}">

    <div class="node-card">
      <div class="node-card__header">
        <p>{{ node.title }}</p>
      </div>
      <div class="node-card__body">
        <div class="node-card__in">
          <p v-if="!init">in</p>
        </div>
        <div v-if="node.nodes" class="node-card__out">
          <p v-for="(childNodes, index) in node.nodes" :key="index">out</p>
        </div>
      </div>
    </div>

    <NodeCards  
    v-for="(child, index) in node.nodes" 
    :node="child" 
    :key="index" />

  </div>
</template>


<script>


export default {
  name: 'NodeCards',
  props: {
    node: Object,
    init: Boolean
  },
};

</script>

<style>

.node-list_general{
  display: flex;
  align-items: center;
}

.node-list_general > *{
  flex: 0 0 250px;
  margin-right: 30px;
}
</style>
