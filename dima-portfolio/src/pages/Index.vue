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
      console.log(this.sectionArray);
    },
    getTotal(h, b, t) {
      return h + parseInt(b, 10) + parseInt(t, 10);
    },
    windowPosition() {
      this.$refs.section.forEach(e => {
        console.log(e.dataset.key + ": " + e.getBoundingClientRect().top);
      });
    },
    throttle(fn, wait) {
      let time = Date.now();
      return function() {
        if (time + wait - Date.now() < 0) {
          fn();
          time = Date.now();
        }
      };
    }
  },
  mounted() {
    this.isMounted = true;
    this.$nextTick(this.measureSectionHeader);
    this.$nextTick(this.measureAllElements);
    // this.$nextTick(
    //   window.addEventListener("scroll", this.throttle(this.windowPosition, 100))
    // );
    // this.measureSectionHeader();
    // this.measureAllElements();
    // this.measureWindow();
    // // this.alertWhenSectionHitsTop();
    // window.addEventListener("scroll", this.throttle(this.windowPosition, 100));
    // // this.alertWhenSectionHitsTop();
    // // this.measureElementPositions();
    // // this.measureAllElements();
  }
};
</script>

<style scoped lang="sass">
@import '../base.sass'


section 
  display: flex
  flex-direction: column
  width: 100%
  height: auto
  background: yellow 
  margin-bottom: 50px
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
.image__container

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