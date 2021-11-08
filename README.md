

# Vue presentation

## Introduction

I used to create various LaTeX (Beamer) presentations with images and videos to demonstrate interactions with user interface of certain program or application.
The biggest advantage was that videos in PDF file were controlled by mouse clicks (paused/played)
so you could comment on the video. 

This was possible thanks to the fact that you could embed Flash (SWF) content into PDF. 
Playback of multimedia files used the built-in Flash Player of Adobe Reader and did not depend on external plug-ins.

Although Adobe no longer supports Flash Player after December 2020 it is still possible to create such presentations but with annoying security warnings and without ability to control video playback.

So I decided to program my own web presentation where I could place anything I like.


## Features
 * built with Vue.js 
 * classic 4:3 layout
 * auto-imports slide components from <code>src/slides</code> directory
 * embed anything into slide (image, svg, video, iframe, ...)
 * control video with mouse - pause, play, show or hide video controls
 * customizable style - change colors, fonts, make animations
 * supports keyboard shortcuts to move to next/previous/first/last slide 
 * displays current slide and slide count in footer, previous/next buttons

## Usage

1. Define your slides inside <code>src/slides</code> directory as Vue SFC components.
You can use <code>DefaultSlide</code> component and <code>VideoWrapper</code> component which handles mouse interactions with video.
2. To make custom slide without <code>DefaultSlide</code> component, add <code>.slide</code> class to root element.
3. Specify order of slides inside <code>App.vue</code>.
4. Place your images, videos, etc. inside <code>src/assets</code> folder.
5. Optionally modify CSS variables inside <code>App.vue</code> to change header/subheader background color easily. 
Main styling resides in <code>VSlides.vue</code>.


### Compiles and hot-reloads for development
```
npm run serve
```

### Builds for production
Generates static HTML, CSS and JS files.
```
npm run build
```

### Example slide

```Vue
<template>
    <DefaultSlide>
        <template v-slot:title>Why Vue.js</template>
        <template v-slot:content>
            <VideoWrapper class="intro-video" :v="v" :p="p" ref="video"></VideoWrapper>
        </template>
    </DefaultSlide>
</template>

<script>
import DefaultSlide from '../DefaultSlide.vue'
import VideoWrapper from "../VideoWrapper.vue";

export default {
  name: "WhyVue",
  components: {VideoWrapper,DefaultSlide},
  data: function(){
    return {
      p: 'Why choose Vue.js.png', //placeholder image
      v: 'Why choose Vue.js.webm', //video file
    }
  }
}
</script>
```

## Keyboard Shortcuts

Be sure to make slides active (click inside).

* Key A (Arrow left) - previous slide
* Key D (Arrow right) - next slide
* Key W (Home) - first slide
* Key S (End) - last slide
* Key C - toggle controls of video (play/mute buttons, time)

## Example 

See my s(a/i)mple [presentation](https://jlubojacka.github.io/vue-presentation/) about Vue. Code for this presentation is located inside <code>/docs</code> folder.

#### What else can you do with such template? Try it out or make something similar.


