<template>
  <b-container id="app">
    <draggable v-model="researchableQuestions" group="questions" @start="drag=true" @end="drag=false" class="card-deck">
    <b-card
      v-for="question in researchableQuestions"
      :key="question.id"
      border-variant="primary"
      :header="question.name"
      header-bg-variant="primary"
      header-text-variant="white"
      align="center"
      no-body
      >
      <draggable v-model="question.findings" group="findings" @start="drag=true" @end="drag=false" class="card-body">
      <b-card
        v-for="finding in question.findings"
        :key="finding.id"
        border-variant="info"
        :header="finding.name"
        align="center"
        no-body
        >
        <draggable v-model="finding.elements" group="elements" @start="drag=true" @end="drag=false" class="card-body">
        <b-list-group-item v-for="element in finding.elements" :key="element.id">
          <b-form-input v-model="element.name" placeholder="Enter your name"></b-form-input>
        </b-list-group-item>
        </draggable>
      </b-card>
      </draggable>
    </b-card>
    </draggable>
    {{researchableQuestions}}
  </b-container>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: 'App',
  components: {
    draggable
  },
  data() {
    return {
      researchableQuestions: [
        {
          id: 1,
          name: "Question 1",
          findings: [
            {
              name: "Find 1 Q1",
              elements: [
                {
                  name: "Element F1 Q1"
                }
              ]
            }
          ]
        },
        {
          id: 2,
          name: "Question 2",
          findings: [
            {
              id: 1,
              name: "Find 1 Q2",
              elements: [
                {
                  id: 1,
                  name: "Element F1 Q2"
                }
              ]
            },{
              id: 2,
              name: "Find 2 Q2",
              elements: [
                {
                  id: 1,
                  name: "Element F2 Q2"
                }
              ]
            }
          ]
        }
      ]
    };
  }
};
</script>
<style scoped></style>
