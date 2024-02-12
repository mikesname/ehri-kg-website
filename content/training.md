---
title: Training & Fellowships
---

This is some **markdown** content with a [link]().

* here
* is a 
* list of
* items

Here is a paragraph with some text in it, and a link to the 
[About]({{< relref "/about" >}}) page.

{{< figure src="../images/doklady-1.png" class="float-right" caption=`
##### Here is a caption for an image

With some text below it`>}}

{{< figure class="fig-side" src="../images/names-2.png" caption=`
##### Another Caption

This figure is on its side.`>}}

### Floating figures

Floating figures can be tricky due to all the inherent complexity
of wrapping text around images, with the added complication of captions.

The theme provides a few classes for this, but things are subject to change:

**fig-float**
: the ``fig-float`` class will float the figure to the left with a default
  width of 50%, except on narrow views.

**fig-right**
: the ``fig-right`` class will float the figure to the right with a default
  width of 50%, except on narrow views.

Additionally, the following shortcode may be useful:

**clear**
: the ``clear`` shortcode is an invisible element that can be used to force
  anything following it to clear previous floating elements.

```go-html-template

{{</* clear */>}} 

```

For example, here is a floated figure and some text that wraps it:

{{< figure src="../images/cards-still-1.png" class="fig-float" caption=`
##### Left floating caption

Using the **fig-float** class will float the figure to the left.`>}}

_This is some text that will go to the right of the previous image._

{{< clear >}}

This text is below the image, because it follows a ``clear`` shortcode.

{{< figure src="../images/doklady-1.png" class="fig-float fig-right" caption=`
##### Right floating caption

Using the **fig-float** _and_ **fig-right** classes will float the figure to the right.`>}}

_Text that wraps to the left of the right-floated image._

{{< clear >}}

##### No caption

To use a floating figure without a caption, simply omit the caption parameter:

{{< figure src="../images/names-2.png" class="fig-float fig-left" >}}

{{< clear >}}

---

Here's a thing the creates a footnote.[^1]

Here's a simple table:

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

Here's a quote:

> This is some text that's in a quotation block

[^1]: This is the footnote