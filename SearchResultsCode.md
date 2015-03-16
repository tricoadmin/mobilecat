### both ###
  * searchbox.html - if js, calls search, else call search\_nojs
  * index.php
  * index.html
  * search\_results.html - iterates through results to get cover & info.
  * cover\_image.php

### js-specific ###
  * index.js
  * search.php - sets search query and search.js, displays search\_main
  * search\_main.html - results page
  * search.js - js to go with results page
  * browse.php - called from search.js to populate actual results

### nojs-specific ###
  * search\_nojs\_main.html - results page
  * search\_nojs.php - pretty much does what browse.php does?