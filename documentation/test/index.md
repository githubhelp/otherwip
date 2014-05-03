---
title:
tags: 
categories: 
published: True
layout: default
js: index
---
---------------------------------------------

list all include tests here

####and again starting with 4 hashes

--------------------------------------------------------


[fully typed out "site.page" hyperlink to testpage ]({{site.page}}test/testpage)

####[fully typed out "site.page" hyperlink to testpage ]({{site.page}}test/testpage)


------------------------------------

###include page 

{%include test/link/page/testpage.md%}

####{%include test/link/page/testpage.md%}

*note - using a nested include (as above) creates an issue with formatting by inserting a line break before trailing parenthesis causing a broken link ref. only difference between the line above and the previous line is a 4hash prefix.

------------------------------------------------------------------------------

###include page (without using .md extensions on include files)

{%include test/link/page/testpage%}

####{%include test/link/page/testpage%}

*note - using a nested include (as above) creates an issue with formatting by inserting a line break before trailing parenthesis causing a broken link ref. only difference between the line above and the previous line is a 4hash prefix.

------------------

[ fully typed out url hyperlink to testsite ](http://jekyllrb.com/)

####[ fully typed out url hyperlink to testsite ](http://jekyllrb.com/)

----------------------------

###include site (url)

{%include test/link/site/site-url.md%}
