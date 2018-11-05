<template>
  <Layout>
    <section v-for='(section,index) in sections' 
            :key="index"
            :class="createSectionClass(section.name)"
            :id="createSectionClass(section.name)">
            <h2 class="section--header">{{ section.name }}</h2>
    </section>
  </Layout>
  
</template>


<script>
import { Pager } from "gridsome";

export default {
  components: {
    Pager
  },
  data() {
    return {
      sections: [
        {
          name: "Visual Development"
        },
        {
          name: "Illustration"
        },
        {
          name: "Sketches"
        },
        {
          name: "Social & Mobile"
        },
        {
          name: "Marketing Posters"
        }
      ]
    };
  },
  methods: {
    createSectionClass(str) {
      const className = str.replace(/\s/g, "").toLowerCase();
      return className;
    }
  }
};
</script>

<style scoped lang="sass">
@import '../base.sass'


section 
  display: flex
  width: 100%
  height: 1000px
  background: yellow
.section--header
  display: flex
  align-self: flex-start
  position: sticky
  top: 10px
  width: 100%
  font-family: $sans-serif
  font-size: 1.8rem
  line-height: 1.3rem
  background: orange
  border-bottom: 2px solid $accent

</style>

<!-- this was the original template layout-->
<!-- <Layout>
    <h1>Welcome to my blog :)</h1>
    <Pager :info="$page.allWordPressPost.pageInfo"/>
    <ul>
      <li v-for="{ node } in $page.allWordPressPost.edges" :key="node._id">
        <h2 v-html="node.title"/>
        <div v-html="node.fields.excerpt"/>
        <router-link :to="node.path">Read more</router-link>
      </li>
    </ul>
  </Layout> -->

<!-- this was underneath the template-->
<!--<page-query>
query Home ($page: Int) {
  allWordPressPost (perPage: 10, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        _id
        title
        path
        fields {
          excerpt
        }
      }
    }
  }
}
</page-query> -->