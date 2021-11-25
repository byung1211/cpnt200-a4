---
title: This is the second code source.
date: 2021-11-22T23:19:03.748Z
code:
  code: >-
    export default {
      router: {
        extendRoutes(routes, resolve) {
          routes.push({
            path: '/users/:id',
            components: {
              default: resolve(__dirname, 'pages/users'), // or routes[index].component
              modal: resolve(__dirname, 'components/modal.vue')
            },
            chunkNames: {
              modal: 'components/modal'
            }
          })
        }
      }
    }
---
  ### [fallback](https://nuxtjs.org/docs/features/file-system-routing#fallback)


  Controls whether the router should fallback to hash mode when the browser does not support history.pushState but mode is set to history.

