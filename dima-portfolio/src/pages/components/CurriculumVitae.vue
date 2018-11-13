<template>
  <section class="cv">
      <h2 class="section--header">Curriculum Vitae</h2>
      <div class="cv__container">
        <div class="cv__container__education">
          <div class="cv__container__education--subheader"><h3>{{ education.subCategoryTitle }}</h3></div>
          <div class="cv__container__education__entry"
               v-for='(e, index) in education.educationEntries'
               :key="index">
              <div class="cv__container__education__entry__left">
                <p><span class="bold-underline">{{ e.title }},</span> {{ e.shortDescription }}</p>
              </div>
              <div class="cv__container__education__entry__right">
                <p><span class="bold">{{ e.dates }}</span></p>
              </div>
          </div>
        </div>
        <div class="cv__container__work">
          <div class="cv__container__work--subheader"><h3>{{ work.subCategoryTitle }}</h3></div>
          <div class="cv__container__work__entry"
               v-for='(w, index) in work.workEntries'
               :key="index">
              <div class="cv__container__work__entry__left">
                <p><span class="bold-underline">{{ w.company }},</span> {{ w.title }}</p>
              </div>
              <div class="cv__container__work__entry__right">
                <p><span class="bold">{{ w.dates }}</span></p>
              </div>
          </div>
        </div>
      </div>
    </section>
</template>

<script>
export default {
  data() {
    return {
      education: {
        subCategoryTitle: "Education",
        educationEntries: [
          {
            title: "Bachelor of Fine Arts",
            shortDescription: "VFX - Visual Development",
            dates: "September 2009"
          },
          {
            title: "Academy of Art University of San Francisco",
            shortDescription: "(AAU) San Francisco, CA",
            dates: "September 2005 - September 2009"
          }
        ]
      },
      work: {
        subCategoryTitle: "Work Experience",
        workEntries: [
          {
            company: "Bluhare Studios",
            title: "Lead Artist",
            dates: "April 2014 - Present"
          },
          {
            company: "Rocket Gaming Systems",
            title: "Artist & Animator",
            dates: "February 2010 - April 2014"
          },
          {
            company: "Dana Production Co.",
            title: "Freelance Artist & Animator",
            dates: "2011 - 2012"
          }
        ]
      }
    };
  }
};
</script>

<style scoped lang="sass">
@import '../../base.sass'


.cv
  display: flex
  &__container 
    width: 80%
    &__education, &__work
      &--subheader
        margin-bottom: 6px
        margin-top: 25px 
        h3
          font-size: 1.5rem
          font-weight: 300
      &__entry
        display: flex 
        margin-bottom: 7px
        justify-content: space-between
        &__left 
          .bold-underline 
            text-decoration: underline
            text-decoration-color: $accent
            font-size: 1.05rem
            font-family: $sans-serif 
            font-weight: bold 
            letter-spacing: .03rem
          p 
            font-family: $sans-serif
        &__right 
          .bold
            font-size: 1rem
            font-family: $sans-serif
</style>