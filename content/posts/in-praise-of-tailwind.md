---
title: "In Praise of Tailwind"
summary: "tailwindcss praise"
date: 2022-08-19
draft: false
tags: [programming]
---

I have been doing "modern" web dev (and here I define modern as the point where there was a marked shift towards primarily using web and browser technologies to build apps) essentially since it existed. There isn't enough positive things I can say about Tailwind, including its team, community, and developers. And while Tailwind is one of those seemingly polarizing tools, I still think the majority of the backlash comes from developers who still just don't "get" it. The ease of which you can simply start from a blank page and create UI components from scratch is bar-none.

But this isn't what this post is about. Those arguments have been made plenty, by people much better at CSS and design than I am.

This praise was spurred by another recent situation where I found myself enjoying using Tailwind. As someone who programs a majority of the time on the backend for their day job, I have to rely on side and learning projects to stay sharp on all the latest and greatest the web is offering, particulary in the area of CSS. I admit I started falling behind, rather, struggled to keep up, a little bit with the advent of flexbox, and grid, especially with the trend of moving a ton of CSS into JS and relying mostly on designer created design systems and UI libraries. Admittedly, getting married and having kids has a little something to do with that as well, but I digress.

So when I crack open a fresh project, whether that's NextJS, SvelteKit, or good ole full stack framework like Phoenix, Laravel, or Rails, the first thing I do is figure out how to get Tailwind installed integrated with whatever framework's build or tooling. Then I begin building my app.

Which brings me to the point of this article. Tailwind offers a great developer experience. However, what I realized just now having started yet another project is the second thing Tailwind does for me: and that is helps me to better learn and understand the CSS I write.

By using the utility classes, and reading them out as I go, I am essentially becoming fluent in Tailwind, which by extension is helping me become fluent in CSS.

Before, when the best practice was to use something like bootstrap or foundation, what was happening was always opaque to me. I understood somewhat that a container set some sort of margin, and auto centered, or I understood that button-primary added styles, shadows, and colors. But I didn't understand "how the sausage was made" so to speak, at least not without diving into the code, which often meant understanding the less or SASS CSS preparser, something I was never really into.

When writing Tailwind components, you are speaking a language of CSS.
{{<highlight html>}}

<div class="flex flex-auto p-6 mb-2 bg-white border border-gray-200 shadow-md rounded-md">
{{< / highlight >}}

is comprehendable to me. "I am creating a flex container, its set to auto, it has 6 px of padding, a 2 px bottom margin, white background, a border, the border is gray, shade 200, it has a medium ox shadow, and medium roundedness"

And by reading it out to myself, this way I am also learning from the visual feedback of seeing what those CSS classes do to the div on the screen.

"Well you could have done that with just CSS by applying a class that has all those properties" or "you can just fiddle around in Chrome or Firefox by using the dev tools" -- sure, and apply it to one or two things here or there. But again, this goes along with the first benefit of Tailwind, in tandem with the fact that I learn by building apps and real things, not by fiddling around. Plus I didn't have this experience using raw CSS either. There is something about learning the Tailwind way that helped chunk the information for me in a way that is easier to digest and remember.

Good job, Tailwind.
