The GIS working group, created in November 2024, was charged with
proposing modifications to the TEI schema to support more detailed,
granular, and standards-based methods of encoding GIS information in
TEI, along with corresponding updates to the Guidelines prose (the full
charge is available at
https://tei-c.org/activities/workgroups/gis-charge/).

Early in 2025, we devised a survey on current practices and preferences,
which was completed by a number of community members particularly
interested in this topic. Based on the survey, we have developed a
proposal for schema modifications allowing support for GeoJSON, WKT,
GML, KML, and other standards within TEI encoding. Our objective has
been to allow encoding patterns which are sufficiently flexible to
support any of the widely-used standards, while applying constraints
which allow for robust interchange. We also need to avoid breaking
backwards-compatibility for those already working with GIS in TEI.

We propose adding a new element, `<geoDef>`, in the TEI header, along
with two attributes, `@geoScheme` and `@level`; we would also add
`@scheme` to the existing `<geo>` element, so that element can point
directly to a `<geoDef>`. The two new attributes would also be available
on `<geo>` itself, for cases where it is more convenient simply to
supply them there. `<geo>` itself would be modified to allow content in
any of the supported GIS standard languages.
