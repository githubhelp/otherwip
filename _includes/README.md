Need some notes here about includes as site is reliant on them they are very important

Maybe create a list to add new includes to and link from here

#### include page/*name*

"pages" are paths to this sites pages, used extensively throughout the page md's and includes, single point to edit every possible link (bar default.html) in one go if an internal page is moved, renamed or deleted.

example setup

    {{site.page}}/folder/page}}

usage syntax

    [CUSTOM-DISPLAYED-TEXT]((% include page/name.md %))


#### include site/*name*

"sites" are paths to external sites, used extensively throughout the page md's and includes, single point to edit every possible link (bar default.html) in one go if an external page is moved, renamed or deleted.

example md

    http://website-name.com/

usage syntax

    [CUSTOM-DISPLAYED-TEXT]((% include site/name.md %))

#### include link/*name*

"links" are ready made commonly used "hyperlinks", they have a "page" or "site" include and already have the more frequently used displayed text set so a shorter syntax can be used

example mds

    [REGULARLY-DISPLAYED-TEXT]((% include site/name.md %))
    [REGULARLY-DISPLAYED-TEXT]((% include page/name.md %))

usage syntax

    (% include link/name.md %)
