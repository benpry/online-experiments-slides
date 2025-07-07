---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
---

# Running experiments online

Ben Prystawski - July 7, 2025

---

# Psychology research, oversimplified

<div class="h-16"></div>

```mermaid {theme: 'forest'}
flowchart LR
  ask["`Come up with
   a question`"]
  des["`Design an 
  experiment`"]
  run["`Run an 
  experient`"]
  an["`Analyze 
  the data`"]
  write["`Write up 
  your results`"]
  ask --> des
  des --> run
  run --> an
  an --> write
```

<v-click>
<Arrow x1="550" x2="520" y1="350" y2="250"/>
<Arrow x1="600" x2="650" y1="350" y2="250"/>

<div class="absolute left-100 bottom-40 text-center">
  We'll cover these two (mostly the first one)
</div>
</v-click>


---

# The plan

1. Overview of running online experiments
2. Prolific
3. Implementing experiments in Qualtrics / JsPsych
4. Data import in R, Python

<!--
Here is another comment.
-->

---

# Online experiments

<div grid="~ cols-2 gap-4">

<div>

Equal parts amazing and infuriating

<v-clicks depth="2">

- Online experiments are fast and conveneint!
  - I've gathered ~400 people worth of data in a single day
- They're (maybe) more representative than university students
- But you need to take some extra steps to ensure data quality
- Some paradigms (e.g. eye-tracking, brain stuff) don't work online

</v-clicks>

</div>

<div class="space-y-6" >

<img v-click="2" src="./assets/large-scale-paper.png" >
<img v-click="2" src="./assets/large-scale-n-participants.png">
<img v-click="3" src="./assets/weirdest-people-in-the-world.png" >

</div>
</div>


---
layout: image-right
image: https://matrix.berkeley.edu/wp-content/uploads/2021/09/mechanical_turk.jpeg
---

# Recruiting people

So where do you get people to do your study?

We recruit people on *crowd-working platforms*.

<v-clicks depth="2">

The two big ones are Amazon Mechanical Turk and Prolific.

Prolific is the most popular among psychologists these days

</v-clicks>


---

<img src="https://app.prolific.com/assets/logo_color-B4lCAEcN.svg" width="200px">

<div class="h-4" />

```mermaid {theme: 'forest'}
flowchart LR
  prolific["`Prolific`"]
  exp["`Your experiment`"]
  prolific-->|experiment link|exp
  exp-->|completion link|prolific
```

<v-clicks>

Anyone can sign up and complete surveys for pay. 

Anyone can pay people to do surveys on Prolific.

You can post a study and choose who it gets shown to based on location, demographics, etc.

Let's take a look at the interface!

</v-clicks>

---
level: 2
---

# Ben's Prolific tips and tricks

<div class="h-4" />

<v-clicks>

- Performance-dependent bonus payments can be useful to motivate participants (you can pay them in bulk too!)
- Checking "microphone required" can help to deter bots (even if your study doesn't actually require a microphone)
- Filter participants based on number of completions and approval rate (>=98%)
- Don't reject people. Request return if they didn't complete the task.

</v-clicks>

---

# The experiment part

<div class="h-4" />

So how do you actually make an experiment to send people to?

<v-clicks>

There are plenty of options, but we're going to cover two:

- Qualtrics
- JsPsych

</v-clicks>


---
class: px-20
---

# Qualtrics

<div class="h-4" />

<div class="grid grid-cols-2 gap-4">

<div>

<v-clicks>

- Qualtrics is a popular platform for making surveys
- It uses a simple drag-and-drop interface 
- There's a lot of more advanced functionality available (e.g writing arbitrary javascript)

</v-clicks>

</div>

<div>

<img src="./assets/qualtrics-interface.png" />

</div>

</div>

---

# Qualtrics tutorial

<div class="h-36" />

<div class="text-2xl">
Do people prefer cats or dogs? Let's make a quick survey to find out!
</div>

<div class="h-8" />

<div>You can follow along at <a href="https://stanforduniversity.qualtrics.com/">https://stanforduniversity.qualtrics.com/</a></div>


---

<img src="https://www.jspsych.org/latest/img/jspsych-logo.jpg" style="width: 200px;">


<div class="grid grid-cols-2 gap-4">

<div>

<div class="h-4" />

<v-clicks>

- a framework for making experiments using javascript
- free and open source
- makes it easier to use version control, share your experiment with others, etc.
- if you know some programming, i would recommend using jspsych for simple experiments.

</v-clicks>

</div>

<div class="relative -top-33">

<img src="./assets/jspsych-screenshot.png" />

</div>

</div>

---

# Considerations when using JsPsych

<div class="grid grid-cols-2 gap-4">

<div>

<span v-click>Where will I host my experiment?</span>

<v-clicks>

- JsPsych experiments are *static*, meaning they contain only HTML, CSS, and JavaScript that runs in the participant's browser.
- Lots of websites let you host static files for free. GitHub Pages is a simple option.

</v-clicks>

<img v-after src="https://logos-world.net/wp-content/uploads/2020/11/GitHub-Logo-700x394.png" />

</div>

<div>

<span v-click>Where will I save my data?</span>

<v-clicks>

- Because the experiment is static, you need to set up somewhere for the data to go.
- There are a few services that let you save data, including cognition.run and proliferate.
- If your lab runs JsPsych experiments, ask your labmates what they use!

</v-clicks>

</div>

</div>


---

# Tips for making good experiments

<div class="h-4" />

<v-clicks>

- People like progress bars and they're easy to implement in Qualtrics and JsPsych
- Comprehension and/or attention checks are often a good idea
- Think about accessibility: if color is important to your task, see if you can use a colorblind-friendly palette.
- Get your labmates / friends to test your experiment before posting it.

</v-clicks>

---

# Getting the data

<div class="h-4" />

If you ran your study on Qualtrics, you can download it as a csv.


<img v-click class="absolute top-50 left-0" src="./assets/qualtrics-export.png" />

<img v-click class="absolute top-20 left-60 w-100" src="./assets/qualtrics-more-options.png" />


---

# You can load the data easily with QualtRics

<div class="flex justify-center">
<div>
<img src="./assets/qualtRics-R.png" class="w-150" />
There's also a Python package called QualtricsAPI.
</div>
</div>


---

# JsPsych – solutions vary

<div class="h-4" />

You can usually click a button to download the data as a csv. Then you can into Python/R.

<div class="h-32" />

<img src="./assets/proliferate-download.png" />

---

<div class="h-48" />

# Questions?

