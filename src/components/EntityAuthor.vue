<template>
  <v-container>
    <div class="font-weight-bold">👩🏻 Author</div>
    <h1 class="text-h3">{{ data.display_name }}</h1>
    <div v-if="data.last_known_institution && data.last_known_institution.id">
      <link-institution :data="data.last_known_institution"/>
    </div>

    <div class="mt-2">
      <link-concept
          v-for="concept in data.x_concepts"
          :key="concept.id"
          :data="concept"
      />
    </div>


    <div class="mt-8">
      <view-in-api-button :id="data.id" />
    </div>
    <v-divider class="mt-12 pt-12" />

    <div class="text-h4">Identifiers</div>
    <id-list :data="data.ids" />

    <div class="text-h4 mt-12">
      {{data.works_count.toLocaleString()}} created works
    </div>
    Click to view in API: <a :href="data.works_api_url" target="_blank">{{data.works_api_url}}</a>



  </v-container>


</template>


<script>
import LinkInstitution from "./LinkInstitution";
import LinkConcept from "./LinkConcept";
import IdList from "./IdList";
import ViewInApiButton from "./ViewInApiButton";

export default {
  name: "EntityAuthor",
  components: {
    LinkInstitution,
    LinkConcept,
    IdList,
    ViewInApiButton,
  },
  props: {
    data: Object,
  },
  data() {
    return {
      foo: 42,
    }
  },
  methods: {},
  computed: {

  },
  created() {
  },
  mounted() {

  },
  watch: {}
}
</script>

<style lang="scss">


</style>