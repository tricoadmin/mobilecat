# IIIParse probably not fully generalizable #

Bob Duncan noted that, "for example, not all III catalogs have 3-column item tables, not everyone uses the label 'status', not everyone uses 'available' to indicate an item's available, not everyone displays medium, not all libraries have scopes, etc., but I see code that refers to these values"

The code is written to TriCo's Tripod catalog, without real research into the variations between structure and vocabulary in different III OPACs.  Scraping the right data depends on the html of the search results page in particular, and is all handled in the IIIParse file.  Libraries will probably need to mess with that code to tweak to their own situations.  It might be better to do this in SiteParse.php, which is a child of IIIParse.

Anyone interested in making that code more general would be welcome to do so!


# Catalog URL and using m.yourcatalog.com #

Bob Duncan notes:

in the SiteParse file we see:
```
    public $catalog_url = "http://www.example.com/";
    public $base_url    = "http://m.example.com/";
```
I realize it's just an example, but I think this could confuse some because if the catalog is www.example.com, then m.example.com may not cut it (just as you couldn't use m.brynmawr.edu even though your catalog is tripod.brynmawr.edu).  And Innovative libraries that use the WAM proxy won't be able to use the m. convention in front of their catalog URL like you did because m.catalog\_url has to resolve to the same IP address as catalog\_url in order for WAM to work.  Suggest you might want something to that effect in the explanation of base\_url on the project page.  (FWIW, we use WAM, our catalog hostname is libcat.lafayette.edu, and I decided to use libcat-m.lafayette.edu for the mobile host because I couldn't think of anything better at the moment.)


**Thank you for the feedback!**