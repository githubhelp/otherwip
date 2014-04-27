links used within mark up should use this syntax

    [DisplayName]({{ site.yaml_id }})
    
    
DisplayName should be a re-usable name to be used mainly as in line link, but can also be used as a title 
site.yml-id is the ref to the url recorded in `_config.yml`

when creating new links use the `site.yml-id` as the links file name in this `_includes/links` folder eg `yml-id.md` and then add them to the `_config.yml` or they won't work.

Try and keep names short, informative and unique.

When viewing the `yml-id.md` the link will look as it will on webpage but get a `404 page` when clicked.

These `_includes` can be used in markdown files using either this syntax

     {% include link/yml-id.md %}

or for a different title this syntax

     [DifferentDisplayName]({{ site.yml_id }})
     
These links will be subject to the usual markdown formatting rules.

####  In HTML though

    <a href="{{site.yml-id}}" >GitHub</a>
    
    <a href="{{site.baseurl}}develop">Develop</a>
