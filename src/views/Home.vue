<template>
  <div class="home">
    <h1>Tree Folder<br>component that calls itself<br>INFINITELY<br>still he has children</h1>
    <button @click="isOpen = true">«Открыть»</button>
    <transition name="bounce">
      <ModalWindow :title="title" :folderTree="folderTree" v-if="isOpen"/>
    </transition>
  </div>
</template>

<script>
// @ is an alias to /src
import ModalWindow from '@/components/ModalWindow.vue'

export default {
  name: 'Home',
  components: {
    ModalWindow
  },
  data: () => ({
    title: "Заголовка",
    isOpen: false,
  }),
  computed: {
    folderTree() {
      return [
        {
          id: 1,
          name: 'Parent-A',
          children: [
            {
              id: 11,
              name: 'Folder-A0',
              children: [
                {
                  id: 111,
                  name: 'Folder-A01',
                },
                {
                  id: 112,
                  name: 'Folder-A02',
                  children: [
                    {
                      id: 1120,
                      name: 'Folder-A020'
                    },
                    {
                      id: 1121,
                      name: 'Folder-A021',
                      children: [
                        {
                          id: 11210,
                          name: 'Folder-A0210',
                          children: [
                            {
                              id: 112100,
                              name: 'Folder-A02100'
                            },
                            {
                              id: 112101,
                              name: 'Folder-A02101'
                            }
                          ]
                        }
                      ]
                    },
                    {
                      id: 1122,
                      name: 'Folder-A022'
                    }
                  ]
                },
                {
                  id: 113,
                  name: 'Folder-A03',
                }
              ]
            },
            {
              id: 12,
              name: 'Folder-01',
            }
          ]
        },
        {
          id: 2,
          name: 'Parent-B'
        },
        {
          id: 3,
          name: 'Parent-C',
          children: [
            {
              id: 31,
              name: 'Folder-C0',
              children: [
                {
                  id: 311,
                  name: 'Folder-C00',
                  children: [
                    {
                      id: 3111,
                      name: 'Folder-C000',
                    },
                    {
                      id: 3112,
                      name: 'Folder-C001'
                    }
                  ]
                },
              ],
              id: 32,
              name: 'Folder-C1',
              children: [
                {
                  id: 321,
                  name: 'Folder-C10',
                  children: [
                    {
                      id: 3211,
                      name: 'Folder-C100',
                    },
                    {
                      id: 3212,
                      name: 'Folder-C101'
                    }
                  ]
                }
              ],
            },
          ]
        },
      ]
    }
  },
  
  methods: {
    
  },
}
</script>

<style>
  .home {
    position: relative;
    width: 100%;
    height: 100%;
  }
  button {
    padding: 10px 20px;
    font-size: 16px;
    font-weight: bold;
    line-height: 20px;
    background-color: darksalmon;
    border: none;
    border-radius: 5px;
    transition: all .5s ease ;
    cursor: pointer;
  }
  button:hover {
    background-color: white;
    color: darksalmon;
    border: 1px solid darksalmon;
  }
  .bounce-enter-active {
  animation: bounce-in .5s;
  }
  .bounce-leave-active {
    animation: bounce-in .5s reverse;
  }
  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }
  
</style>
