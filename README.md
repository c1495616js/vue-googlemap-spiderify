# vue-googlemap-spiderify

###### tags:  `vue` `vue2-google-maps`


![](https://i.imgur.com/Cv18s6l.png)


[![Edit Vue Template](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/v6x046lwl0)

## Introduction

I designed the web for gas sensor, and there are a lot of sensors in a same building which means they are in same coordinates.

And we use google map cluster, so it can't separate no matter how you zoom in.

Therefore, we make this change by math.  [Logarithmic spiral](https://en.wikipedia.org/wiki/Logarithmic_spiral)

![](https://i.imgur.com/LRmtbmL.png)

## Key function

```javascript=
 // key function
    function tranform (lng, lat, j, cnt) { // helper
      const l = 10e-5
      const theta = 2 * Math.PI / cnt

      const t = j * theta
      const r = l * Math.log(cnt/4*j+1) * theta
      // const r = (Math.E)^( t )

      const x = r * Math.cos(t)
      const y = r * Math.sin(t)
      return {
        lng: lng + x,
        lat: lat + y
      }
    }
  },
```

### Setup

#### Use your own google map api key

```javascript=
Vue.use(VueGoogleMaps, {
  load: {
     key: 'USE_YOUR_GOOGLE_API_KEY',     
  }
});
```

#### Add markers here

```javascript=
generateMarkers(){
    const n1 = 20;
    [...Array(n1).keys()].forEach(j => {
      this.markers.push(marker1)
    })

    const n2 = 10;
    [...Array(n2).keys()].forEach(j => {
      this.markers.push(marker2)
    })
  }
},
```
