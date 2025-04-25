This presentation will share the current state of the TEI's GIS Working Group work, outlining the group's objectives, 
current recommendations, and the rationale behind them. Created in November 2024, the GIS Working Group (GIS-WG) was charged with
proposing modifications to the TEI schema to support more detailed,
granular, and standards-based methods of encoding geospatial data in
TEI, along with corresponding updates to the Guidelines prose (the full
charge is available at
https://tei-c.org/activities/workgroups/gis-charge/).

The group has made good progress so far. Early in 2025, we devised a survey on current practices and preferences,
which was completed by a number of community members particularly interested in this topic. We have also received feedback and discussion from the community during the March TEI Community Call. Drawing on this feedback and informed by existing practices, the GIS-WG has developed a proposal for schema modifications allowing support for GeoJSON, WKT, GML, KML, and other standards within TEI encoding. We have sought to ensure that these proposed changes are sufficiently flexible to 
support widely-used standards,  appropriately constrained to facilitate robust interchange, and backwards compatible with existing practices. 

In our short paper, we will share our current thinking and proposed modifications. We propose expanding `<geo>` to allow content in any
of the supported geographic standards and creating a new element, `<geoDef>,` to allow for centralized definitions of geographic schemes. These two elements will both be members of a new class of attributes, which will specify the encoding scheme used, its version, and, to promote interchange, the level at which the geographic scheme is being implemented. 





