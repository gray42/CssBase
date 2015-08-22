# Looking back on my journey through CSS Development  
> A succession of stages, processes, operations, or units.

    1. Introduction
    2. Between the sheets                       -- Use Seperate CSS files
    3. You talking to me?                       -- Commenting your code
        3.1. You have to draw a line somewhere  -- Seperate Code Blocks
    4. Get yourself in order!                   -- CSS Property Order
    5. All of my tin soldiers in a row          -- Example Files
    6. The End                                  -- EOF

<!--    3.1. What's up, Doc?                    -- CSS DocBlocks             -->

## Introduction

Recently I realized that I have been hacking together websites for more than a 
decade.

Over the years there are many things I have read, tried, used and discovered.

The last year or two I've been mostly busy in the back-end of applications but 
recently I've been getting back more into the front-end so it felt like a good 
idea to take stock of what I learned over the years.

## Between the sheets

I started out just putting all of my styles in one sheet but as the projects 
became bigger, I reached a point where that just wasn't maintainable. So, after 
trying a couple of variations I settled on dividing my CSS between seperate 
files like this:

 - Base-Elements
 - Layout Rules
 - Design Rules
 - CSS Helper Classes
 - Modules Folder (with an individual file for each module)
 - Themes Folder  (if needed)

Once this was set I never really looked back untill I encountered Scalable and 
Modular Architecture for CSS (or SMACSS for short). I really enjoyed the idea 
behind [SMACSS][smacss.com]. It makes the following distinction:

 - Base Rules
 - Layout Rules
 - Module Rules
 - State Rules
 - Theme Rules

This got me thinking that I should take the time to reflect on my own way of 
dividing CSS into sections.

After some thought I realized that my CSS Helper classes should just go in the 
Section they're helping, either Base, Layout or Design. 

Something else that got me thinking, is that I tend to put a lot of what would 
be called a Module in SMACSS in my "Design" Section. This also includes "Default 
Theme" styling. I do tend to put the styling for any "Module" that is not part 
of a site's core in seperate files. 

I tend to keep what SMACSS calls "State" together with the module the state can 
be invoked on. Although I can see the merits of keeping the states in a seperate 
section I am not yet completely convinced.

For now that would leave me with the following distinction which seems like an 
improvement over my previous preference:

 - Base-Elements
 - Layout Rules
 - Base-Theme
 - Modules Folder (with an individual file for each module)
 - Themes Folder  (if needed)

[smacss.com]: http://smacss.com/
[READ-THIS]: http://csswizardry.com/2012/11/code-smells-in-css/

## You talking to me?

I've always been in favour of commenting my stylesheets as much as I can. Not 
just at a low level (for instance noting _why_ a certain hack for `IE6` is used), 
but also outlining at a block or module level what is expected of a certain set 
of CSS rules (and _why_).


<!--
### What's up, Doc?
                            CSS DocBlocks
********************************************************************************
*                           HIER GEBLEVEN                                      *
********************************************************************************
-->

[kss]: http://warpspire.com/kss/styleguides/

### You have to draw a line somewhere

One of the other things I have tried many, *many* variations of is rulers (or
horizontal dividers) to separate distinct blocks of CSS code. The latest form I
have settled on is this:


    /********( Meta Information )**************************************************/

    /*=======( Top Level )========================================================*/

    /*-------( Sub Level )--------------------------------------------------------*/

    /*.......( Lower Sub Level )..................................................*/

    /* - - - ( Even Lower Level ) - - - - - - - - - - - - - - - - - - - - - - - - */

    /* . . . ( Lowest Sub Level ) . . . . . . . . . . . . . . . . . . . . . . . . */

    /********( EOF )***************************************************************/

In case you are wandering what the `EOF` is about, I like to mark all and any 
file with an end-marker. That way (although this doesn't occur often at all 
anymore), when a file doesn't get correctly transported or copied to another 
server you have a way of telling. Also, especially in development, anything that 
doesn't really have a place can be put below the line by other developers and 
the individual responsible for cleanup can put it in the right place.

Especially when working in a (larger) team, styling doesn't get squashed into 
places where it doesn't belong. This way it is easier to keep track of changes, clean things up and it can save a lot trouble.

Other forms I have toyed with include splitting the title and the rulers over
two lines :

    /*  Top Level
    ==============================================================================*/

    /* Sub Level
     -----------------------------------------------------------------------------*/

        ...

and using one single form of ruler but indenting it to distinguish its level:

    /********( Top Level )*********************************************************/

        /********( Sub Level )*****************************************************/

        ...

Both these (and other variations) did not strike the right balance between a
[visual cue][wikipedia.sensory-cue] and [succinctness][dictionary.succinctness].
I'm sure there is another solution that is more powerful and graceful, but for
now I am sticking to what I've got.

[wikipedia.sensory-cue]: http://en.wikipedia.org/wiki/Sensory_cue
[dictionary.succinctness]: http://www.merriam-webster.com/thesaurus/succinctness


## Get yourself in order!

There is a strongly advocated (but [not-so broadly used][css-tricks-poll]) 
practice to order properties alphabetically. The strongest argument for this is 
that alphabetical order makes it easier to find existing properties or add new 
ones, as the alphabet is the same for everyone. The order that seems most 
logical for properties to go in, however, differs from every individual to the 
next.

Personally, I don't adhere to this view. In fact, I'm a strong *opponent* of 
this. I prefer to order my selectors outside-in. The main reasons for my 
opposing view is the fact that, as I tend to divide the properties for an 
element across several files, you need to know what goes where anyway and the 
order I stick to is documented thoroughly. The need to use vendor prefixes also 
plays amock with the "easy to scan, easy to find" paradigm. Another thing that 
tends to happen is that I have a habit of putting "new" (as in CSS level 3 and 
up) selectors and the end, to make a clear distinction between which styles 
work _everywhere_ and _always_ and which ones don't.

Hell, I might even put a ruler between them. With an actual comment!

I'm crazy like that.

If you prefer alphabetic order, that's fine (be consistent, whatever you choose) 
but if you do favour things in order I would strongly advise you to stick to 
[the declaration order as defined in "Idiomatic CSS"][idiomatic-css#declaration-order]. 

I came to the order I tend to use for my selectors long before I'd even heard of 
Idiomatic CSS but it is almost identical. 

I guess there is a common logic to it after all: 

 - Positioning
 - Display
 - Box model
 - Colors and Typography
 - Other


<!--
    A full example of this would be:
    
********************************************************************************
*                           HIER GEBLEVEN                                      *
********************************************************************************
-->

[css-tricks-poll]: http://css-tricks.com/poll-results-how-do-you-order-your-css-properties/
[idiomatic-css#declaration-order]: https://github.com/necolas/idiomatic-css#declaration-order


## All of my tin soldiers in a row

As mentioned, I tend to split things that belong in different sections into 
seperate stylesheets. I also tend to document in each stylesheet what my 
intentions are. Since I prefer to have my selectors in a certain order I add 
this in the comments too. Putting all of this together I ended up with the 
files below as a base for any new project I work on.

### `application.css`

In an development environment I tend to use a single file to include the various 
other files from. In a testing or production environment [you don't want `@import` 
rules lying about][stevesouders-dont-use-import], so the imported files are all 
concatenated and minified and replace the import rules. That way there is no 
need to alter the HTML between development and production stages.

If you use a CSS pre-processor like SASS or LESS this is even less of a problem.

*File contents:*

    @charset "UTF-8";

    @import "01.base-elements.css";
    @import "02.layout.css";
    @import "03.design.css";

[stevesouders-dont-use-import]: http://www.stevesouders.com/blog/2009/04/09/dont-use-import/
### `01.base-elements.css`

Any reset or change to HTML tags go in this file. I start out with a default and
then alter that to the needs of the project. As I learn new or better ways to do
things I expand and alter this file. For instance, I have been meaning to trim 
the fat of this file a bit by incoporating more from [normalize.css](https://github.com/necolas/normalize.css/blob/master/normalize.css)

This document contains a foundation for all the HTML elements. It resets
attributes that different browsers have different defaults for. It also has
some font normalization and adds some base styles.

Using a combination of Eric Meyers Reset, the YUI CSS Modules and a healthy
dose of plain old common sense

    http://meyerweb.com/eric/tools/css/reset/
    http://developer.yahoo.com/yui/base/
    http://developer.yahoo.com/yui/fonts/
    http://developer.yahoo.com/yui/reset/
    http://en.wikipedia.org/wiki/Common_Sense_(pamphlet)


*File contents:* [01.base-elements.css](CSS-Base-Setup/01.base-elements.css)


### `02.layout.css`
Layout consist of the CSS properties that have to do with the display, flow,
positioning, and dimensions of elements. This includes margins and padding.

Semantically, one could argue that giving something a border is a matter of
design. Because borders do influence an elements size, `border-width` *does*
belong here. However, `border-color` and `border-style` do *not* belong
here. Instead, border style and colour should be declared in the design
related CSS files.

This does mean using the shorthand property for `border` is impossible.

*File contents:* [02.layout.css](CSS-Base-Setup/02.layout.css)

### `03.Base-Design.css`
Design consist of the CSS properties that have to do with the visual styling
of elements and typography:

*File contents:* [03.Base-Design.css](CSS-Base-Setup/03.Base-Design.css)

## The End!
