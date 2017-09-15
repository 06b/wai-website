---
title: Animations
order: 4
wcag_success_criteria:
  - 2.2.2
first_published: "May 2015"
editors:
  - Eric Eggert: "https://www.w3.org/People/yatil/"
  - Shadi Abou-Zahra: "https://www.w3.org/People/shadi/"
contributors:
  - The Education and Outreach Working Group (<a href="https://www.w3.org/WAI/EO/">EOWG</a>)
support: Developed with support from the <a href="https://www.w3.org/WAI/ACT/">WAI-ACT project</a>, co-funded by the <strong>European Commission <abbr title="Information Society Technologies">IST</abbr> Programme</strong>.
---

Provide users with control over animations in the carousel. Pausing animation is essential for people who find movement distracting or who need more time to read.

## Add Play/Stop button

Provide a button to allow users to stop and resume animation. The example below illustrates how such a button can be marked-up. The button label and its function changes, depending on whether the animation is currently running or not.

{::nomarkdown}
<%= demo %>
{:/}

{::nomarkdown}
<%= code_start('','While animation is running') %>
{:/nomarkdown}

~~~html
<button data-action="stop"><span class="visuallyhidden">Stop Animation </span>￭</button>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start('','While animation is stopped') %>
{:/nomarkdown}

~~~html
<button data-action="start"><span class="visuallyhidden">Start Animation </span>▶</button>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

{::nomarkdown}
<%= demo :middle %>
{:/}

A [working demo example](working-example.html) for this code is available.

{::nomarkdown}
<%= demo :end %>
{:/}

{::nomarkdown}
<%= notes_start %>
{:/nomarkdown}

**Note:** The JavaScript only replaces the value of the `<button>` element and its attributes. Replacing the entire button would result in loss of keyboard focus.

{::nomarkdown}
<%= notes_end %>
{:/nomarkdown}

## Pause on mouse hover and keyboard focus

Pause the carousel animation when the mouse pointer is hovering over the carousel or when it receives keyboard focus. Pausing on mouse hover is useful for people who need more time to read the content and makes it easier to click links in the carousel. Keyboard users do not lose their position when the carousel is paused.

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~js
carousel.addEventListener('mouseenter', suspendAnimation);
carousel.addEventListener('mouseleave', startAnimation);

carousel.addEventListener('focusin',
  function(event) {
    if (!hasClass(event.target, 'slide')) {
      suspendAnimation();
    }
  }
);
carousel.addEventListener('focusout',
  function(event) {
    if (!hasClass(event.target, 'slide')) {
      startAnimation();
    }
  }
);
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

{::nomarkdown}
<%= notes_start %>
{:/nomarkdown}

**Note:** The [`focusin`](https://www.w3.org/TR/DOM-Level-3-Events/#event-type-focusIn) and [`focusout`](https://www.w3.org/TR/DOM-Level-3-Events/#event-type-focusout) events are defined in the [W3C Document Object Model (DOM) Level 3 Events Specification](https://www.w3.org/TR/DOM-Level-3-Events/) (Working Draft) and implemented in many browsers. Firefox needs [a short polyfill](full-code.html) at the time of publication of this tutorial.

{::nomarkdown}
<%= notes_end %>
{:/nomarkdown}

## Hiding transitioning elements from assistive technologies

During transitions, the current and next items are visible. This also means that those two items are available to assistive technologies, with the current item disappearing, which can be confusing to screen reader users.

In the following example, the item that is being activated gets an `in-transition` class that makes it visible. The `aria-hidden` is attribute set to `true` to hide the item from assistive technologies. When the transition completes, the `aria-hidden` attribute is removed.

{::nomarkdown}
<%= code_start('', 'JavaScript') %>
{:/nomarkdown}

~~~js

slides[new_next].className = 'next slide'
  + ((transition == 'next') ? ' in-transition' : '');
slides[new_next].setAttribute('aria-hidden', 'true');

slides[new_prev].className = 'prev slide'
  + ((transition == 'prev') ? ' in-transition' : '');
slides[new_prev].setAttribute('aria-hidden', 'true');

slides[new_current].className = 'current slide';
slides[new_current].removeAttribute('aria-hidden');
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}
