<template>
  <div id="builderEditorDrawers">
    <!--Inner Loading-->
    <inner-loading :visible="loading"/>
    <!--Block drawers-->
    <q-drawer bordered v-model="drawers.blocksList" :width="540" hide-scrollbar>
      <blocks-list/>
    </q-drawer>
    <q-drawer bordered v-model="drawers.blocksShow" :width="540" overlay hide-scrollbar>
      <blocks-form/>
    </q-drawer>
    <q-drawer bordered v-model="drawers.blockAttributes" :width="540" hide-scrollbar>
      <attributesForm/>
    </q-drawer>
  </div>
</template>
<script>
import Vue, {defineComponent, computed} from "vue";
import editorStore from '@imagina/qbuilder/_store/editor'
//Components
import blocksList from '@imagina/qbuilder/_components/editor/drawers/block/list.vue'
import blocksForm from '@imagina/qbuilder/_components/editor/drawers/block/form.vue'
import attributesForm from '@imagina/qbuilder/_components/editor/drawers/block/attributes.vue'

export default defineComponent({
  setup() {
    return {
      loading: computed(() => editorStore.state.loading),
      drawers: computed(() => editorStore.state.drawers)
    }
  },
  props: {},
  components: {
    blocksList,
    blocksForm,
    attributesForm
  },
  watch: {},
  mounted() {
    this.$nextTick(function () {
    })
  },
  data() {
    return {
      projectName: this.$store.getters['qsiteApp/getSettingValueByName']('core::site-name'),
      logo: this.$store.state.qsiteApp.logo
    }
  },
  computed: {},
  methods: {
    //init
    init() {
    }
  }
})
</script>
<style lang="stylus">
#builderEditorDrawers
  .drawer-title
    background-color $primaryBuilder
    color white
    font-size 18px
    display flex
    align-items center
    justify-content space-between

  .q-page-container{
    padding-left 0 !important
  }

  .padding-drawer-content
    padding 16px 24px

  .q-drawer
    padding: 0px !important
    border-right: 0px

  .q-drawer-container
    padding: 0px !important
</style>
