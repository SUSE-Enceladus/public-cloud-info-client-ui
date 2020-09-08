Public Cloud Info Service Web UI
================================

Provides a web page that users can interact with to see tabular data about 
SUSE provided public cloud images. 


Running Locally
---------------

The UI can be run on any system that has a basic web server. For development
purposes using the python3 http server is an option.

```
python3 -m http.server 8080 --bind 127.0.0.1
```

After starting up the web server, navigate in a browser to
http://localhost:<port>  , in the instance above http://localhost:8080


Development
-----------

The pint-cloud-info-client-ui primarily consists of the index.html file
that is in the root of the repository. 

Parts of the eos design system ( https://suse.eosdesignsystem.com/ ) are
incorporated via css snippets maintained under assets/css/eos-imports ,
along with a small number of pintui specific css overrides. The pint
web ui leverages css from www.suse.com for consistent look & feel, for
details see the imports in index.html

Data caching
------------

The pint web UI makes use of local storage to cache data for up to 24 hours
after a query has been made. As the xml content for public cloud providers
can be quite large, the data cache keeps the load time down during a timeframe
where its unlikely that changes have occured on the backend.

Before creating a PR, it is recommended to test changes with the
`cache_timeout` variable in index.html set to a low value to ensure that the
changes work correctly with freshly loaded data.
