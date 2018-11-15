<template>
  <Layout :layoutSectionArray="sectionArray" v-if='isMounted'>
    <section v-for='(section,index) in sections' 
            :key="index"
            :class="createSectionClass(section.name)"
            :id="createSectionClass(section.name)"
            ref="section"
            :data-key="index"
            >
            <h2 class="section--header"
                ref='sectionheader'>{{ section.name }}</h2>
      <div class="image__container" 
           ref='imagecontainer'>
        <div v-for="(image, index) in section.images" :key="index">
              {{ index }}
              <p>{{ image.url }} </p>
              <p>{{ image.alt }}</p>
              <hr>
            </div>
      </div>
            
    </section>
    <section class="about">
      <h2 class="section--header">About</h2>
      <p class="about--text content--section">Eu ullamco fugiat veniam anim id nostrud nostrud do eu aliquip. Tempor deserunt ex nisi dolore labore exercitation id id sit culpa cupidatat. Magna aliquip elit elit ea mollit amet voluptate. Adipisicing est in commodo consectetur. Tempor Lorem incididunt dolore commodo consequat. Eu ullamco fugiat veniam anim id nostrud nostrud do eu aliquip. Tempor deserunt ex nisi dolore labore exercitation id id sit culpa cupidatat. Magna aliquip elit elit ea mollit amet voluptate. Adipisicing est in commodo consectetur. Tempor Lorem incididunt dolore commodo consequat. Eu ullamco fugiat veniam anim id nostrud nostrud do eu aliquip. Tempor deserunt ex nisi dolore labore exercitation id id sit culpa cupidatat. Magna aliquip elit elit ea mollit amet voluptate. Adipisicing est in commodo consectetur. Tempor Lorem incididunt dolore commodo consequat. Eu ullamco fugiat veniam anim id nostrud nostrud do eu aliquip. Tempor deserunt ex nisi dolore labore exercitation id id sit culpa cupidatat. Magna aliquip elit elit ea mollit amet voluptate. Adipisicing est in commodo consectetur. Tempor Lorem incididunt dolore commodo consequat. Eu ullamco fugiat veniam anim id nostrud nostrud do eu aliquip. Tempor deserunt ex nisi dolore labore exercitation id id sit culpa cupidatat. Magna aliquip elit elit ea mollit amet voluptate. Adipisicing est in commodo consectetur. Tempor Lorem incididunt dolore commodo consequat.</p>
    </section>
    <app-curriculum-vitae></app-curriculum-vitae>
    <app-contact></app-contact>
  </Layout>
  
</template>


<script>
import { Pager } from "gridsome";
import Contact from "./components/Contact.vue";
import CurriculumVitae from "./components/CurriculumVitae.vue";

export default {
  components: {
    Pager,
    appContact: Contact,
    appCurriculumVitae: CurriculumVitae
  },
  data() {
    return {
      isMounted: false,
      sectionHeights: [],
      sectionArray: [],
      sections: [
        {
          name: "Visual Development",
          images: [
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            }
          ]
        },
        {
          name: "Illustration",
          images: [
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            }
          ]
        },
        {
          name: "Sketches",
          images: [
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            }
          ]
        },
        {
          name: "Social & Mobile",
          images: [
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            }
          ]
        },
        {
          name: "Marketing Posters",
          images: [
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            },
            {
              url: "this is a test image",
              alt: "testing alt text"
            }
          ]
        }
      ]
    };
  },
  methods: {
    createSectionClass(str) {
      const className = str.replace(/\s/g, "").toLowerCase();
      return className;
    },
    measureSectionHeader() {
      const sectionHeaderHeight = this.$refs.sectionheader[0].scrollHeight;
      this.setImageSectionMargin(sectionHeaderHeight);
    },
    setImageSectionMargin(number) {
      this.$refs.imagecontainer.forEach(el => {
        el.style.paddingTop = `${number}px`;
      });
    },
    measureAllElements() {
      let counter = 0;
      this.$refs.section.forEach(e => {
        const style = e.currentStyle || window.getComputedStyle(e);
        const eHeight = e.scrollHeight;
        console.log(eHeight);
        const eMarginBottom = style.marginBottom;
        const eMarginTop = style.marginTop;
        const eTotalHeight = this.getTotal(eHeight, eMarginBottom, eMarginTop);
        console.log(eTotalHeight);
        this.sectionArray.push({
          id: counter,
          height: eTotalHeight
        });
        counter++;
      });
    },
    getTotal(h, b, t) {
      return h + parseInt(b, 10) + parseInt(t, 10);
    }
  },
  mounted() {
    this.isMounted = true;
    this.$nextTick(this.measureSectionHeader);
    this.$nextTick(this.measureAllElements);
  }
};
</script>

<style scoped lang="sass">
@import '../base.sass'


section 
.section--header
.image__container
  @include navsnap 
    padding: 0px 10px
.content--section 
  max-width: 80%
  @include edgesnap 
    max-width: 100%
    // padding: 0px 15px
    padding-right: 15px
  @include navsnap 
    padding-right: 0px 
    padding: 0px 10px
.about--text 
  margin-top: 25px
  font-family: $sans-serif

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