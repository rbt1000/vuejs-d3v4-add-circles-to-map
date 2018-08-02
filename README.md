# vuejs-d3v4-add-circles-to-map
d3v4 Changed dramatically from d3v3.   There aren't alot of examples that I could find for using vue.js with d3d4 for mapping, 
so I created this to help with the learning curve.

This is based on this great example: https://github.com/CorpGlory/d3vue  and expects this to be installed first. 

1) Install  https://github.com/CorpGlory/d3vue and validate that you have it running.
2) Add these files from this repo:   
  -src
    - basic-map-bubble
          - mapone.vue
          - index.vue
3) Edit this file with the new route
   -router
    - demo.js
    
     and add this route:
     
  {
    name: ' map: bubble tooltip & events',
    path: '/basic-map-bubble',
    folder: true,
    component: require('d3-components/basic-map-bubble/index')
  },
    
    
