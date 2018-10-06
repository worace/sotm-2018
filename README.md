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
  * [Population Density Open Dataset](https://code.fb.com/core-data/open-population-datasets-and-open-challenges/)
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

# Day 2

## Keynote - Mapping to Fight FGM

[Neema Meremo](https://twitter.com/neemameremo)

* [Types of FGM](http://www.endfgm.eu/female-genital-mutilation/what-is-fgm/)
* 70%+ in some portions of Tanzania
* [Hope For Girls & Women](https://hopeforgirlsandwomen.wordpress.com/)
  * [Twitter](https://twitter.com/hopeforgirlstz)
  * Provides safe houses for girls
  * **Lack of reliable maps in rural areas hinders safehouse access**
* Rural Tanzania very sparsely mapped
  * Dar Es Salaam vs Rural Tanzania
* [Crowd2Map](https://crowd2map.wordpress.com/) [Twitter](https://twitter.com/crowd2map)
* Combination of Remote and Local Volunteers
* RVs set up tasks and determine which areas contain buildings to be mapped
  * [MapSwipe](https://mapswipe.org/)
* LVs validate and add new buildings using [Maps.Me](https://maps.me/) and [FieldPapers](https://wiki.openstreetmap.org/wiki/Field_Papers)
* Coordination between RVs (often educated, technically proficient) + LVs (low schoo)
* Smartphones still a novelty in many of the areas being mapped
* [HOT MicroGrant](https://www.hotosm.org/updates/2017-04-20_hot_microgrants_2017_results) helped purchase smartphones for mapping ([announcement](https://crowd2map.wordpress.com/2017/04/22/crowd2map-has-been-awarded-a-hot-microgrant/))
* Program giving women access to smartphones to participate in the mapping initiative
  * Carries risk of community backlash, violence against women, rape, assault
  * Men often try to dominate training programs; not enough equipment to go around
  * Traditional sexism characterizes access to technology in Tanzania
* [YouthMappers](https://www.youthmappers.org/)
* 3k+ girls finding safehouses thanks to mapping efforts
* 75% reduction in FGM in Tanzania
* Trained 300+ new mappers through the program
* [UNFPA Mapathon](https://ungaguide.com/listing/mapathon-at-unfpa-to-help-eliminate-female-genital-mutilation/)
* **Ongoing Needs**

## Filling in the Gaps with the Mapillary API

[Christopher Beddow](https://twitter.com/c_beddow)

* [Mapillary](https://www.mapillary.com/)
* OSM Needs:
  * More + Better Data
  * Freshness
  * Accuracy
  * Completeness
  * Verification
* Evidence-based mapping
* [Potlach](https://en.wikipedia.org/wiki/Potlatch_(software))
* [Vespucci](https://wiki.openstreetmap.org/wiki/Vespucci)
* Rise of machine-assested mapping
  * Gives access to greater scale, detail, etc
  * Still needs verification
* "Machine Enhancement"
  * Machine finds notable data, human fixes the map
* Mapillary image processing
  * Object detection (currently 100+ known entity types)
  * GPS information allows spatial placement of objects within images
* Common OSM Gaps
  * Often have basic structure (roads, buildings, etc)
  * Missing details and attributes
  * Freshness -- mapillary images give timestamps to assess freshness
* [JOSM Mapillary plugin](https://wiki.openstreetmap.org/wiki/JOSM/Plugins/Mapillary) [GitHub](https://github.com/JOSM/Mapillary)
* Mapillary API
  * [Docs](https://www.mapillary.com/developer/api-documentation/)
  * Can query for images by id, bounding box
  * Can query for sequences of images
* Data Positioning
  * [OpenSfM](https://github.com/mapillary/OpenSfM)
  * Image Detections API - gives breakdown of features within an image by percentage and location
  * CV allows depth and positioning estimation from images to produce more precise image interpretation
* [Mapillary Vector Tiles](https://www.mapillary.com/developer/tiles-documentation/) [Blog Post](https://blog.mapillary.com/update/2015/05/27/vectortiles.html)
  * [Can now be loaded into iD](https://medium.com/@vershwal/vector-tile-support-for-openstreetmaps-id-editor-40b1cb77f63b)
  * Layers:
    * Imagery
    * Unmapped roads
    * Traffic signs
    * image detections
* [Pic4Review](https://wiki.openstreetmap.org/wiki/Pic4Review)
* [go2mapillary](https://github.com/enricofer/go2mapillary) QGIS plugin


## OSM for Disaster Management: City Wide Mapping Project (Jakarta,Surabaya and Semarang)

[Harry Mahardhika Machmud](https://twitter.com/harrymahar), Humanitarian OpenStreetMap Team Indonesia

* Mapped 3 big cities in indonesia - Jakarta, Surabaya, Samarang
* [PDC - Pacific Disaster Center](https://www.pdc.org/)
* [Humanitarian OpenStreetMap Team (HOT)](https://www.hotosm.org/)
* Mapping Objectives
  * Everything...
  * POIs, green space, roads, buildings, infrastructure, waterways, health facilities, etc
* Timeline
  * Surabaya: Oct 2016 - Feb 2017
  * Jakarta: March 2017 - Nov 2017
  * Samarang: Jan 2018 - July 2018
* Preparation
  * Coordination with local governments; getting surveying permit letters
  * Prioritize mapping goals
  * Recruit mappers - Hire + Train local people (important to have local knowledge)
* Equipment
  * Local survey map
  * Satellite imagery (USAID?)
  * JOSM settings
* **Process**
  * Team members collecting data on mobile devices
  * Verify and upload data to OSM via JSOM
  * [OpenDataKit](https://opendatakit.org/)
  * [OpenMapKit](http://openmapkit.org/)
  * [Process Video](https://drive.google.com/file/d/1u-Ohda5Ddd9yrq7wu4gQlO2DjmrOlxUn/view)
* Progress
  * [Surabaya](bit.ly/surabayachanges)
  * [Jakarta](bit.ly/jakartachanges)
  * [Semarang](bit.ly/semarangchanges)
* Data In use by other tools
  * https://petabencana.id/map/jakarta
  * http://inaware.bnpb.go.id/inaware/

## Building AI-Assisted Mapping Tools: Progress And Lessons Learned

[Drew Bollinger](https://twitter.com/drewbo19), Development Seed

* Identify Coverage potential by comparing current OSM building coverage to ML-predicted building presence
* [LabelMaker](https://github.com/developmentseed/label-maker)
* [Google DeepLab v3](https://github.com/tensorflow/models/tree/master/research/deeplab)
* 256x256px tiles for analysis
* Building Masks from [SpaceNet](https://spacenetchallenge.github.io/) for training
* Dealing with error -- easy for sat images and OSM to be slightly misaligned
  * Use total area as a metric for assessing coverage
* [linematch](https://github.com/mapbox/linematch)
* [Blog Post](https://medium.com/devseed/mapping-buildings-with-help-from-machine-learning-f8d8d221214a)
* [Jaccard Index (intersection over union)](https://en.wikipedia.org/wiki/Jaccard_index) [for object detection](https://www.pyimagesearch.com/2016/11/07/intersection-over-union-iou-for-object-detection/)

## Analytic Support for Contributors: Defining Levels of Automation for Machine Learning Applied to Crowdsourced Mapping

Ryan Lewis
In-Q-Tel CosmiQ Works / SpaceNet

* SpaceNet: "A corpus of commercial satellite imagery and labeled training data to use for machine learning research"
* SpaceNet 4 Pillars
  * Data - releasing remote sensing data
  * Competitions - sponsoring open analytics competitions
  * Code - publishing research on emerging analytic frameworks
  * Tools - sharing open source software tools
* [Public Datasets](https://spacenetchallenge.github.io/)
  * 30cm WV-3 single strip images for 4 cities:
    * Las Vegas
    * Paris
    * Shanghai
    * Khartoum
* Competitions
  * Bldg footprints in Rio with 50cm imagery
  * Bldg footprints in Las Vegas, Paris, Khartoum, Shanghai
  * Road Extraction + Routing - LV, Paris, Khartoum, Shanghai - includes some new metrics for assessing coverage and quality
* SpaceNet 4 - Off Nadir Analysis
  * 27 images from nadir to 53 degrees off nadir
  * 117k building footprint labels
  * 3k km of road network labels
* Challenges for CV / ML in context
  * Targeting different types of information can require running multiple algorithms
  * Varying computational cost + performance across different models / application
* ML + Mapping - translating to GIS formats
  * Instance segmentation -> line or polygon
  * Object classification -> geometric features with properties
  * "Sub-feature classification" -> OSM Classification scheme (`building=...`)
* Evaluation metrics
  * Object count
  * Jaccard/IoU
  * F1 score w/IoO threshold >= 0.5
  * Cumulative IoU
  * pixel-based f1-score
  * [PoLiS metric](https://ieeexplore.ieee.org/document/6849454)
  * **qualitative feedback from mappers**
* [AWS SageMaker](https://aws.amazon.com/sagemaker/)
* **Level of Difficulty** for ML Mapping
  * useful to clarify levels of automation (similar to how autonomous vehicle industry breaks down automation targets)
  * how do mappers validate projections from ML models?
* Levels
  * 0 - crowdsource improvements; no automation (Traditional OSM approach)
  * 1 - Tasking Manager Planning Assistance (e.g. [Dev Seed building coverage tasker](https://medium.com/devseed/mapping-buildings-with-help-from-machine-learning-f8d8d221214a))
  * 2 - Some Label Suggestions w/ human completion
  * 3 - Complete Label Suggestions w/human validation (Machine provides geometry + populated labels. Human evaluates performace on a per-entity basis...i.e. complete validation)
  * 4 - Complete mapping with human validation (Mapping larger areas that can't be validated exhausitvely; confident enough to rely on spot-checking / partial validation)
  * 5 - Complete mapping

##  Semi-Automated Map Editing

Fayven Bastani, MIT CSAIL

> consider machine-assisted map editing, where automatic map inference is integrated with existing, human-centric map editing workflows.

* [Abstract](http://nms.lcs.mit.edu/papers/index.php?detail=256)
* Goal: Overcome coverage gaps in rural areas
* 2 decades of research toward map inference from aerial imagery and gps traces
* Adoption is slow
  * **Error rates** - Still too high for fully automated approaches
  * Many automated systems take a "from scratch" approach -- unresolved questions around combining inference with existing map information
  * **Tooling** - lack of integration with existing map editing tools (eg OSM iD / JOSM etc)
* **Machine-Assisted Map Editing**
* Prototype: infer streets within a region; provide all of this information to user to edit. Make corrections on a per-segment basis.
  * Speed was not significantly faster than simply tracing (~ 1.1x)
  * Not much faster to validate than to just trace
* Breaking down by context
  * **Sparse coverage**: add major arterial roads
    * major roads are long, so manual tracing is slow.
    * Validation-based approach can be more beneficial here
  * **High coverage**: reduce time searching for unmapped roads
    * Getting from 98% coverage to 100% coverage
    * Hard to find small amounts of missing coverage in already heavily-mapped areas; ML can save time here
* Giving the user focus via these tools can improve mapping significantly
* [RoadTracer](https://www.csail.mit.edu/news/mitqcri-system-uses-machine-learning-build-road-maps) [source](https://github.com/mitroadmaps/roadtracer) [paper](https://roadmaps.csail.mit.edu/roadtracer.pdf)














