# YouTube search is on the Check Step

The Owner wants search, not a curated watch list. Search uses the YouTube Data API (`search.list`) with a query built from the current Check Step and “E46.” Hits are Suggestions. They become Citations only if the Owner pins one.

This fights least-invasive order: YouTube will surface regulator videos. The query stays step-shaped (`E46 check window fuse`) so we do not search “E46 window regulator” on the fuse step. Official search is capped (YouTube documents 100 `search.list` calls per day on a default project), so search is a button, not a scrape on every page load.
