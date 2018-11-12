<template>
  <section class="contact">
      <h2 class="section--header">Contact</h2>
      <div class="contact__container">
        <div class="contact__container__left">
          <div class="contact__container__left__brand"></div>
          <div class="contact__container__left__blurb"></div>
          <div class="contact__container__left__subcategory">
            <div class="contact__container__left__subcategory--subheader">
               <p>Email</p>
            </div>
            <div class="contact__container__left__subcategory--content">
                <a :href="`mailto:${email}?subject=Email from Website`">
                  {{ email }}
                </a>
            </div>
           </div>
          <div class="contact__container__left__subcategory">
            <div class="contact__container__left__subcategory--subheader">
               <p>Blog</p>
            </div>
            <div class="contact__container__left__subcategory--content">
                <a :href="`${blog}`" target="_blank">
                  {{ blog }}
                </a>
            </div>
           </div>
           <div class="contact__container__left__subcategory">
            <div class="contact__container__left__subcategory--subheader">
               <p>Social</p>
            </div>
            <div class="contact__container__left__subcategory--content">
                <a v-for="(social, index) in socialLinks"
                   :key="index" 
                   :href="social.url">
                  <img :src="social.image.src" :alt="social.image.alt">
                </a>
            </div>
           </div>
        </div>
        <div class="contact__container__right"></div>
      </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: "dimaduchet@gmail.com",
      blog: "blogspot.com/dimaduchet",
      socialLinks: [
        {
          name: "Behance",
          url: "https://www.behance.net/dimaduchet",
          image: {
            src: require("../../assets/behance-icon.svg"),
            alt: "Link to Behance artist portfolio page"
          }
        },
        {
          name: "LinkedIn",
          url: "https://www.linkedin.com/in/dima-duchet/",
          image: {
            src: require("../../assets/linkedin-icon.svg"),
            alt: "Link to LinkedIn profile"
          }
        },
        {
          name: "Instagram",
          url: "https://www.instagram.com/dimaduchet/",
          image: {
            src: require("../../assets/instagram-icon.svg"),
            alt: "Link to Instagram profile"
          }
        }
      ]
    };
  }
};
</script>

<style scoped lang="sass">
@import '../../base.sass'

.contact 
  &__container 
    &__left 
      &__brand 
      &__blurb 
      &__subcategory
        margin-top: 18px 
        &--subheader 
          font-family: $sans-serif
          font-size: 1.4rem
        &--content, a, a:visited
          font-size: 1.1rem
          margin-top: 4px
          text-decoration: none
          color: black
          font-family: $serif
          img 
            height: 30px
            margin-right: 7px
        
    width: 100%

</style>