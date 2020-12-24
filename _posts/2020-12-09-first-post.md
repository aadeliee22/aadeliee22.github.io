---
title: "Prototype"
toc: true
toc_sticky: true
date: 2020-12-09 08:26:28 -0400
categories: 
  - practice
use_math: true
---

## Plan
My plan for using this blog is
- Update my outputs : presentation, projects, etc.
- CV : I will take some time here.
- Record what I have done while lab experiences.

## Record of my trials.
### images:
![On June 18, 2019](/assets/images/june-18-2019-hubble-v-nebula.jpg){: width="50%" height="50%"}

To insert images, I made folder named `/assets/images` folder and put certain images there.
```
![text here](/assets/images/filename.jpg){:width="50% height="50%}
```
and 50% each for smaller photo.

### url 
My website: <https://aadeliee22.github.io/> by `<https://blah.blah>`

### Math
Pythagorean theorem $a^2 + b^2 = c^2$ and Hamiltonian for ising model,
$$
\mathcal{H} = J\sum_{\langle i, j\rangle} s_i s_j + B\sum_i s_i
$$

To insert latex formula is not quite simple for me... The reference is here: <https://mkkim85.github.io/blog-apply-mathjax-to-jekyll-and-github-pages/>
1. Change` _config.yml`... but I still don't know how to change this file and rebuild/reload the whole github pages, since I just created this repository not installing jekyll or ruby. Someone who knows the answer please inform me! :(
```markdown
# Conversion
markdown: kramdown
highlighter: rouge
lsi: false
excerpt_separator: "\n\n"
incremental: false
```
Luckly, my yml file didn't need any changes.

2. Make `mathjax_support.html`
```html
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    TeX: {
      equationNumbers: {
        autoNumber: "AMS"
      }
    },
    tex2jax: {
    inlineMath: [ ['$', '$'] ],
    displayMath: [ ['$$', '$$'], ['\\(', '\\)'] ], <!-- '\\(' part is important for me. -->
    processEscapes: true,
  }
});
MathJax.Hub.Register.MessageHook("Math Processing Error",function (message) {
	  alert("Math Processing Error: "+message[1]);
	});
MathJax.Hub.Register.MessageHook("TeX Jax - parse error",function (message) {
	  alert("Math Processing Error: "+message[1]);
	});
</script>
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
```

3. Change `_layouts/default.html` by this:

```html
{% if page.use_math %}
  {% include mathjax_support.html %}
{% endif %}
```

4. Yes, it is over! But not totally...
If you want to use math formula, than you need to add `use_math: true` at front-matter of the post.
Then inline formulas: `$...$` and display mode: `$$...$$` will work.


