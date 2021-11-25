---
title: This is a first code snippet.
date: 2021-11-22T03:30:25.138Z
code:
  code: >-2
      components: { cpnt200_header, Footer },
      async asyncData ({ $content }) {
        const page = await $content('home').fetch()
        const blog = await $content('blog/2021-11-21-this-is-a-test-post').fetch()
        const profile = await $content('profile/2021-11-22-map-picture-uploads-profile_image-png-dateofbirth-sun-nov-21-2021-20-21-25-gmt-0700-mountain-standard-time-introduction-hello-i-am-a-good-person-thinking-to-make-the-world-better-name-alex-byung-uk-an-information-i-am-taki').fetch()
        const code = await $content('code-snippet/2021-11-21-this-is-a-code-snippet-from-the-conig-yml').fetch()
        return {
          page, blog, profile, code
        }
      }
---
This is just a sample code. never mind.
