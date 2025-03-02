# cbft command-line

Command-line help is available by running...

    ./cbft --help

That will print out usage/help output...

    cbft: couchbase full-text server
    
    Usage: cbft [flags]
    
    Flags:
      -auth AUTH
          authentication method for cbft requests
      -b, -bindHttp ADDR:PORT
          local address:port where this node will listen and
          serve HTTP/REST API requests and the web-based
          admin UI; default is '0.0.0.0:8095';
          multiple ADDR:PORT's can be specified, separated by commas,
          where the first ADDR:PORT is used for node cfg registration.
      -c, -cfg, -cfgConnect CFG_CONNECT
          connection string to a configuration provider/server
          for clustering multiple cbft nodes:
          * couchbase:http://BUCKET_USER:BUCKET_PSWD@CB_HOST:CB_PORT
               - manages a cbft cluster configuration in a couchbase
                 3.x bucket; for example:
                 'couchbase:http://my-cfg-bucket@127.0.0.1:8091';
          * simple
               - intended for development usage, the 'simple'
                 configuration provider manages a configuration
                 for a single, unclustered cbft node in a local
                 file that's stored in the dataDir;
          * metakv
               - manages a cbft cluster configuration in couchbase metakv store;
                 environment variable CBAUTH_REVRPC_URL needs to be set
                 for metakv; for example:
                 'export CBAUTH_REVRPC_URL=http://user:password@localhost:9000/cbft';
          default is 'simple'.
      -container PATH
          optional slash separated path of logical parent containers
          for this node, for shelf/rack/row/zone awareness.
      -data, -dataDir DIR
          optional directory path where local index data and
          local config files will be stored for this node;
          default is 'data'.
      -e, -extra, -extras EXTRAS
          extra information you want stored with this node
      -h, -H, -?, -help 
          print this usage message and exit.
      -options KEY=VALUE,...
          optional comma-separated key=value pairs for advanced configurations.
      -register STATE
          optional flag to register this node in the cluster as:
          * wanted      - make node wanted in the cluster,
                          if not already, so that it will participate
                          fully in data operations;
          * wantedForce - same as wanted, but forces a cfg update;
          * known       - make node known to the cluster,
                          if not already, so it will be admin'able
                          but won't yet participate in data operations;
                          this is useful for staging several nodes into
                          the cluster before making them fully wanted;
          * knownForce  - same as known, but forces a cfg update;
          * unwanted    - make node unwanted, but still known to the cluster;
          * unknown     - make node unwanted and unknown to the cluster;
          * unchanged   - don't change the node's registration state;
          default is 'wanted'.
      -s, -server URL
          URL to datasource server; example when using couchbase 3.x as
          your datasource server: 'http://localhost:8091';
          use '.' when there is no datasource server.
      -staticDir DIR
          optional directory for web UI static content;
          default is using the static resources embedded
          in the program binary.
      -staticETag ETAG
          optional ETag for web UI static content.
      -tags TAGS
          optional comma-separated list of tags or enabled roles
          for this node, such as:
          * feed    - node can connect feeds to datasources;
          * janitor - node can run a local janitor;
          * pindex  - node can maintain local index partitions;
          * planner - node can replan cluster-wide resource allocations;
          * queryer - node can execute queries;
          default is ("") which means all roles are enabled.
      -uuid UUID
          optional uuid for this node; by default, a previous uuid file
          is read from the dataDir, or a new uuid is auto-generated
          and saved into the dataDir.
      -v, -version 
          print version string and exit.
      -weight INTEGER
          optional weight of this node, where a more capable
          node should have higher weight; default is 1.
    
    Examples:
      Getting started, using a couchbase (3.x) on localhost as the datasource:
        ./cbft -server=http://localhost:8091
    
      Example where cbft's configuration is kept in a couchbase "cfg-bucket":
        ./cbft -cfg=couchbase:http://cfg-bucket@CB_HOST:8091 \
               -server=http://CB_HOST:8091
    
    See also: http://github.com/couchbase/cbft
    
---

Copyright (c) 2015 Couchbase, Inc.
