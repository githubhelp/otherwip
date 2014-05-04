---
title:
tags: 
categories: 
published: True
layout: default
js: index
---

[oem gateway](http://openenergymonitor.org/emon/user/1531#oem gateway)

---------------------------------------------

list all include tests here

####and again starting with 4 hashes

--------------------------------------------------------


[fully typed out "site.page" hyperlink to testpage ]({{site.page}}test/testpage "This is a test for the link hover over" )

####[fully typed out "site.page" hyperlink to testpage ]({{site.page}}test/testpage "This is a test for the link hover over" )


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

[ fully typed out url hyperlink to testsite ](http://jekyllrb.com/ "This is a test for the link hover over" )

####[ fully typed out url hyperlink to testsite ](http://jekyllrb.com/ "This is a test for the link hover over" )

----------------------------

###include site (url)

[this is a hybrid link with a full typed display name and include tag]({%include test/site/site-url.md%})

#### [this is a hybrid link with a full typed display name and include tag]({%include test/site/site-url.md%})

next uses yml not url

[this is a hybrid link with a full typed display name and include tag]({%include test/site/site-yml.md%})

#### [this is a hybrid link with a full typed display name and include tag]({%include test/site/site-yml.md%})

----------------------------

###include link (url)

{%include test/link/site/site-url.md%}

#### {%include test/link/site/site-url.md%}

This is a line off text with {%include test/link/site/site-url.md%} nested into it.

---------------------------------------------

[testlink.md]({%include testlink.md%})

####[testlink.md]({%include testlink.md%})

----------------------------



{{ 'Shopify' | link_to: 'http://shopify.com' }}











