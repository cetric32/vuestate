<template>
  <div class="hello row">
    <div class="left col-md-6">
      <h1>{{title}}</h1>
      <form @submit.prevent="addLink">
          <input type="text"
           class="form-control shadow rounded-bottom m-1 "
           placeholder="Add Link"
           v-model="newLink"
           >
      </form>
      <ul class="list-group m-3">
        <li class="list-group-item" v-for="(link,index) in links" :key="index">
          {{link}}
          <button type="button"
          class="ml-2 btn btn-danger"
          @click="removeLinks(index)"
          >Remove</button>
        </li>
      </ul>
    </div>
    <div class="right col-md-6">
      <stats />
    </div>
  </div>
</template>

<script>
import Stats from '@/components/Stats.vue'
import { mapState, mapMutations, mapActions } from 'vuex'

export default {
  name: 'HelloWorld',
  data () {
    return {
      newLink: null
    }
  },
  computed: {
    ...mapState([
      'title',
      'links'
    ])
  },
  components: {
    Stats
  },
  methods: {
    ...mapMutations([
      'ADD_LINK'
    ]),
    ...mapActions([
      'removeLink'
    ]),
    addLink: function () {
      this.ADD_LINK(this.newLink)
      this.newLink = null
    },
    removeLinks: function (link) {
      this.removeLink(link)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.right{
  background-color: #f2e7de;
}

</style>
