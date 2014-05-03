Need some notes here about includes as site is reliant on them they are very important

Maybe create a list to add new includes to and link from here

#### include page/*name*

"pages" are paths to this sites pages, used extensively throughout the page md's and includes, single point to edit every possible link (bar default.html) in one go if an internal page is moved, renamed or deleted.

example 
    {{site.*page*}}/*folder*/*page*}}

usage syntax
    [DISPLAYED-TEXT]((% include page/name %))


#### include site/*name*

"sites" are paths to external sites, used extensively throughout the page md's and includes, single point to edit every possible link (bar default.html) in one go if an external page is moved, renamed or deleted.

example 
    http://*website-name.com/*

usage syntax

    [DISPLAYED-TEXT]((% include site/name %))

#### include link/*name*

"links" are ready made commonly used "hyperlinks" they already have the displayed text set and include a "page" or "site"  

    (% include link/name %)
