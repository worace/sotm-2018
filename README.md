# Day 1 (Friday October 5, 2018)

## Transportation as a Service – Using OSM at Lyft to Improve Your Ride

[Alexandra Kazakova](https://twitter.com/alexnk26) and [Renee Park](https://twitter.com/reneehpark), Lyft

* Using trace data to detect road geometry inaccuracies
* Lyft OSM Goals
  * Localization (where is the user)
  * Time + Distance estimates
  * Routing + Navigation
  * Freshness + Accuracy
* Lane inference - Using satellite imagery to overlay lanes onto existing road network
* Autonomous Vehicles - Resolution + Accuracy needs are much higher
  * Lane dividers -- 10cm resolution
* OSM Lane + Turn Restriction data -- important for navigation and AV, but coverage is currently poor
* AV: Relies on combining richer map data with live on-device sensor processing

## OSM In Every Car… Closer Than You May Think

[Philipp Kandal](https://twitter.com/apphil)

* Intensive mapping experiments -- thorough mapping in canada
* "Embedded Navigation" - Enhanced mapping with sufficient metadata to inform automotive safety systems (speed limits, lanes, turn restrictions, etc)
* Detroit prototype - intensive mapping in Detroit to enable Embedded Navigation experiments
* Automotive Sensors
  * Much richer data available from cars vs. phones
  * Better gyroscopes, steering wheel angle, better cameras, better GPS
  * Enables image-based processing like sign detection
* Using internal tools to generate OSM changesets, which can then be validated in JSOM and submitted to OSM
* [Telenav Camera Lending Program](https://www.openstreetmap.us/2018/05/camera-lending-program/)
* [Waylens Dashcam](https://www.waylens.com/horizon)

## Automotive Panel

**Speakers**
* [Emily Schwartz (uber)](https://twitter.com/emkschwartz)
* [Kevin Webb](https://twitter.com/kvnweb)
<!-- -->
* [SharedStreets](https://sharedstreets.io/)
* [NACTO](https://nacto.org/)
* [Uber Movement](https://movement.uber.com)
* [ODBL](https://opendatacommons.org/licenses/odbl/)
* [GTFS - General Transit Feed Specification](https://en.wikipedia.org/wiki/General_Transit_Feed_Specification)

## Validation Of The Users, By The Users, For The Users

[Matthew Gibb](https://twitter.com/giblet22) - Radiant Solutions

* [JOSM BuildingsTools](https://wiki.openstreetmap.org/wiki/JOSM/Plugins/BuildingsTools)
* [Tasking Manager](https://tasks.hotosm.org/) ([wiki](https://wiki.openstreetmap.org/wiki/OSM_Tasking_Manager))
* [MapRoulette](http://www.maproulette.org/) ([wiki](https://wiki.openstreetmap.org/wiki/MapRoulette))
* [developmentseed/scoreboard](https://github.com/developmentseed/scoreboard)

## POI Data Illuminated

Diana Shkolnikov, StreetCred

* [@dianashk](https://twitter.com/dianashk)
* [StreetCred](https://www.streetcred.co/)
* StreetCred is developing a "self-sustaining open protocol for POI data collection and distribution."
* POI Difficulties:
  * **Coverage**
  * Freshness
  * Quality
  * Accessibility / Licensing
* Measurement by absolute number can be misleading
* OSM: 39k POIs in NYC
* Measuring relative/proportional coverage is important -- need the denominator
* Using [geohashes](https://dzone.com/articles/designing-spacial-index) to grid the world.
* Strong correlation between road network + POI location
* POI Density by `highway` tag
  * `primary` - 74
  * `secondary` - 46
  * `tertiary` - 35
  * etc...
* Use these estimates to extrapolate total density in an area like NYC -- for these numbers would expect to find 185k POIs ([Blog Post](https://www.streetcred.co/blog/2018/8/1/invisible-places))
* [Observable Notebook](https://beta.observablehq.com/@dianashk/poi-estimation/2)
* [MapNYC](https://mapnyc.streetcred.co/) (+ [MapDetroit](https://mapnyc.streetcred.co/detroit))

## OpenStreetMap as an AWS Public Dataset and Its Uses

Joe Flasher, Amazon Web Services

* [AWS Public Datasets](https://aws.amazon.com/opendata/public-datasets/)
  * [Registry](https://registry.opendata.aws/)
  * [Use](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-public-data-sets.html)
  * Storage is free. Can mount as a volume from EC2 as with other S3 services. Pay only for compute or additional storage you incur.
  * 15-16 PB of data available
  * Datasets are submitted
* [OSM Dataset](https://registry.opendata.aws/osm/)
  * OSM Planet PBF file
  * Updated weekly
  * Can be accessed as an [ORC file](https://orc.apache.org/) for Athena or Hive access
  * Can be downloaded from s3: `aws s3 cp s3://osm-pds/2017/planet-170501.osm.pbf .`
* [Example Application - Map Tiles](https://aws.amazon.com/blogs/publicsector/develop-and-extract-value-from-open-data/)
* [Snowball Edge](https://aws.amazon.com/snowball-edge/) - potential disaster response applications
  * [DroneDeploy](https://www.dronedeploy.com/)
  * [OpenAerialMap](https://openaerialmap.org/)
  * [PortableOSM](http://posm.io/)
* [SpaceNet Challenge](https://spacenetchallenge.github.io/)
  * [Building Detector Challenge](https://spacenetchallenge.github.io/datasets/spacenetBuildings-V2summary.html)
* [LandSat on AWS](http://landsatonaws.com/)

## The Machine Mappers Are Coming

Eric Gundersen, Mapbox

* Came to OSM from intl development; needed better mapping.
* Mapbox bringing OSM to broader audience through customer integrations (Facebook, etc)
* Reaping benefits of real-time sensor data coming from mobile users
* Demo'd some client-side automated mapping software
* Feature detection on device allows limited transmission (don't need to send raw imagery)
* Mapbox telemetry receiving 225M miles of GPS traces per day(?)
* Question for OSM: How does approach to receiving automated data change to handle this information
* [OSM Editing Standards](https://wiki.openstreetmap.org/wiki/Editing_Standards_and_Conventions)
* [OSM Good Practice](https://wiki.openstreetmap.org/wiki/Good_practice)
* "HD Maps" -- modern mapping approach focusing on richer spatial data:
  * Enhanced road network including lane data, traffic, turn restrictions, etc
  * Vector based. Efficient; can be processed on device
  * Fast to process and compact to transmit

## OSM at Facebook

[Drishtie Patel](https://twitter.com/Drish_T) + [Saurav Mohapatra](https://twitter.com/mohaps)

* Facebook OSM Growth - originally 22 countries
* Now showing OSM maps in most countries
* Focuses for working with OSM data
  * Importing from planet files
  * Additional validation, profanity filtering, vandalism prevention, etc.
  * Enhancements on top of OSM base map -- ML-powered road detection, etc
* **Profanity Detection**
  * Curated list of 40k words in 43 languages
  * Found 84k matches within the OSM dataset
  * Filtered down to 2k via standardized rules, which could then be manually approved
  * Identified 139 actual problems, which were fixed in OSM
* [OSMCha](https://osmcha.mapbox.com/) - Changeset validator
* ML - OCR Vandalism checks for profanity
* **Road Identification**
  * Started with Thailand; now working on Indonesia
  * Using High identification threshold to pick a centerline and avoid false positives
  * Follow up with trimming + merging process to fill gaps
  * Remove "islands" where roads don't connect to the rest of the network
  * Convert data into OSM format and open in iD
  * Using HotOSM Tasking Manager to divide work for editors
  * triple validation - editor, validator, publisher
  * Using forked iD editor with some JOSM features integrated
  * [wiki article](https://wiki.openstreetmap.org/wiki/AI-Assisted_Road_Tracing)
  * [mapillary id editor](https://blog.mapillary.com/news,/update/2014/08/19/id.html) (not sure this is what facebook is using but seems like a similar idea)
* Assessing Coverage
  * [Population Density Open Dataset](https://code.fb.com/core-data/open-population-datasets-and-open-challenges/**
  * Use this information to inform areas of focus for mapping
* Mobius - "Continuous Ingestion of OSM Data"
  * Challenges: Vandalism, volume
  * Diffing or partial application is challenging
  * Use SCM-like model to evaluate individual changesets in isolation
  * "Tinder for Changesets" - Evaluate world before and after a given changeset
* Mobius Boston Prototype
  * 4k OSM Changesets
  * Compressed to 2k "logical" changesets
  * 48% are single-feature change -- can be very quickly reviewed
  * 5% of changesets contain 85% of features changed (wow!)

## Historical Change Mapping using OSM-as-a-Platform

[Marc Farra](https://twitter.com/kamicut), [Development Seed](https://developmentseed.org/)

* **Treat OSM as a Google Doc**
  * Collaborative
  * Blank Slate
  * Quick to create / delete
  * Ephemeral
* [osm-seed](https://github.com/developmentseed/osm-seed) - Infrastructure project to facilitate ad-hoc, independent OSM instances
* Use case: Mapping historical change in World Bank "Special Economic Zones"
* Using satellite imagery + OSM Seed instances to map changes in environment over time
* OSM Pros:
  * Clear + established data schema
  * Great tooling (JOSM, iD)
  * Tasking manager
* OSM Cons:
  * Focused on current state of the world
  * Limited metadata can't handle historical information
* OSM Seed approach: Separate instances for each point in time
* Why not _x_
  * [POSM](http://posm.io/) - borrowed some Docker configuration from this project
  * [Open Historical Map](https://wiki.openstreetmap.org/wiki/Open_Historical_Map)
  * Independent traditional editors (QGIS, ArcGIS)
* [Kubernetes](https://kubernetes.io/) for container orchestration
* [Tegola](http://tegola.io/) - Vector Tile Server
* Other uses
  * [Palestine Open Maps](https://palopenmaps.org/#/) - OSM Mapping on top of paper maps background
  * [Vietnam OpenRoads](https://developmentseed.org/projects/openroads/) - Independent OSM instance to enable working with private data
  * [TeachOSM](http://teachosm.org) - Stress-free training with isolated sandbox environments

## OSM vs. Blockchain to Tell the Historical Mapping Story

[Jeremy Lechtzin](https://twitter.com/jeremylechtzin)

* [StreetDeets](http://streetdeets.com/)
* [Old Brooklyn Heights](https://oldbrooklynheights.com/)
* [NYPL Historical Maps & Data](https://www.meetup.com/historical-data-and-maps-at-nypl/)
* [NYC Spacetime Directory](https://spacetime.nypl.org/)
* [Open Historical Map](https://wiki.openstreetmap.org/wiki/Open_Historical_Map)
* [OSM & Online Time Machines](https://www.slideshare.net/gwhathistory/osm-and-online-time-machines-sotm-us-2012-pdx)
* [Mapping History on OpenStreetMap](https://www.slideshare.net/frankieroberto/mapp-history-on-open-street-map)
* Challenging to find tools to combine spatial and historical information
* OSM focuses on "real time or something close to it"
* Need for multiple base layers
* [80s.nyc](http://80s.nyc/)
* [Urban Archive](http://urbanarchive.nyc/)
* [OldNYC.org](https://www.oldnyc.org/)
* How to place historical information on a contemporary map? Often things won't correlate with current state of the world.
* BlockCHain + Place Data
  * [Propy](https://propy.com/)
  * [Meridio](https://www.meridio.co)
  * [Foam](https://foam.space/)
  * [StreetCred](https://www.streetcred.co/)
  * Comparisons to property deeds -- these often contain timestamps, provenance chains (grantor to grantee), and geographic context (location of property)

## The OpenStreetMap US Camera Lending Program

[Martin van Exel](https://twitter.com/mvexel)


* [OpenStreetCam](https://openstreetcam.org/)
* [OSM Wiki Entry](https://wiki.openstreetmap.org/wiki/OpenStreetCam)
* Launched 2016
* 170M images so far
* Originally mobile phone cameras; now using some dashcams as well
* Open Source iOS/Android apps
* 4.5M km covered
* Images free under CC-by-SA license
* Integrates with OSM editor to enable mapping based on OSC imagery
* Recognizes 90+ US sign classes
* ML models are open source; trained from ~50k annotated images
* [Waylens Horizon](https://www.waylens.com/horizon)
  * Includes custom OSM integrations for OSM account linking, OSC uploading, etc
* Benefits of dedicated camera
  * Doesn't overheat
  * Better + wider camera
  * Keeps phone free for other use
  * Stores data on device and uploads when connected to wifi
* Lending program
  * 20 cameras
  * Standard loan period 3 months
  * Keep the camera if you capture 1 million points!
  * Support via slack
  * 10 points for new roads; 1 point for repeat coverage