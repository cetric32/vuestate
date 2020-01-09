<template>
  <div class="stats">
    <h1>
      A different component
    </h1>
    <p>
        There are currently {{countLinks}} links
    </p>
    <button type="button"
    @click="removeAllLinks"
    >Remove All Links</button>
    <p>{{msg}}</p>

  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'Stats',
  data () {
    return {
      msg: null
    }
  },
  computed: {
    ...mapGetters([
      'countLinks'
    ])
  },
  methods: {
    ...mapActions([
      'removeAll'
    ]),
    removeAllLinks () {
      this.removeAll().then(() => {
        this.msg = ' They have been removed'
      })
    }
  }

}
</script>

<style scoped>
button {
  width: 100%;
  padding: 10px;
  margin-top: 30px;
  background: none;
  border: 1px solid lightgray;
  outline: 0;
  cursor: pointer;
}

</style>
