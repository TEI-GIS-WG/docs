# TEI-GS WG Meeting Notes

## 2025-04-11

**Attending**: JT, MH

### Summary
The main idea is that there are three things that need to be specified: the `@standard`, the`@version` of that standard, and the level/object/granularity at which you're using that standard. (Also encourage `@ref` to point at a formal standard, if not defined.) 

We need to think about what to name this to make it clear that this attribute is defining the formal name of the container as defined in the standard. In the case of XML content, perhaps there is no need to specify the container if there's a single root element, since you can just include the complete element, but if the content of `<geo>` is a fragment, then a container should be specified. If it's a JSON structure, then not including a level implies that the content is a complete self-defining object complying with the standard in `@standard`.

Overall, we are currently thinking:

* Create a class of attributes for declaring and defining the use of geographic standards
* Update or create a new element for declaring and defining the use of a standard (either repurposing `<geoDecl>` or create a `<geoDef>`)
* Retain `<geo>` and do not create a new element (to allow for backwards compatibility)

### Agenda

* Discussing survey results and recapping discussion from most recent TEI community call
* We need to determine whether we create a new element (called geometry) or significantly change the existing geo element
* What is it that we're trying to constrain and should we be trying to implement rules based on scheme?
    * If your `@scheme` is GML, must have an element in the GML namespace?
    * If you `@scheme` is KML, must be namespace?
* But question emerges of at what level people can embed information: e.g. with GeoJSON, would you start at a key (e.g. "geometry" or actually valid JSON)?
* We need a mechanism that enables to say exactly what you're doing and how
   * You need to be able to specify a level (a `@level` or some such)
   * Attributes like scheme and schemeVersion, but redefined with (open?) list of which geoDef and geo have. 
   * Some examples of what this might look like (recognizing that the attribute names and such are all still in flux)
    ```xml
     <geoDef geoScheme="WKT" level="POINT"/> <!--two coordinates will do-->
     <geoDef geoScheme="GeoJSON" level="geometry">
         <desc><!--Any particular description that one would
               want to provide about what this definition means
               in the context of their project--></desc>
      </geoDef>
    ```
* Also discussing potential contribution for TEI2025 (due near end of April):
    * Decided on proposing a short paper outlining the problem and our potential solution. JT to draft. 
* Will schedule next meeting of WG to be held within next few weeks to finalize short paper submission.

## 2025-01-24

**Attending**: JT, MH, GR

### Summary

* Created survey in the TEI's Google Drive
* JT to solicit feedback on draft form from colleagues, and will ping the GIS group once finished
* Aim to send out by Feb 10th with close date of Feb 27 (with one or two reminders)

### Agenda

* Meeting times / scheduling
* Survey to TEI-L:
    * is this just an email? an open discussion? or is it a more formal survey? 
    * Do you encode GIS information in your TEI files?
    * How do you encode GIS information in your TEI files?
    * Do you use `<geo>`? If so, what do your `<geo>`s look like?
        * What is it wrapped in? E.g. in what contexts are you using `<geo>`?
    * If you use some other non-TEI mechanism, why is that?
    * Created survey in Google Drive
        * JT to solicit some feedback re: wording etc
        * Once wording is finalized, test submission
        * Once done, send out to TEI-L
* Aim to send out survey by Feb 10
* Next meeting: Feb 28 @ 09:00 PST 

## 2024-11-26

**Attending**: JT, MH

### Summary

Although we really do need to do a survey to determine what people are currently doing and what changes they might be amenable to, we are basically tending towards the view that:
 * We can most easily maintain backward compatibility while providing better options for new encoding by adding a new `<geometry>` element. 
 * The new element could carry `@scheme` to specify which specific encoding standard is being followed in it.
 * It would allow text and anyXML so that e.g. GML, KML, and GeoJSON could be directly encoded in it.
 * Based on `@scheme`, Schematron could do basic checks of JSON well-formedness, element namespaces, and so on.
 * In the context of `<location>`, the new `<geometry>` element would be assumed/constrained to contain geographic reference encoding (while not constrained to the actual earth, as `<geo>` currently is, allowing fictional and extra-terrestrial geographies to be handled). 
 * However, standards like GeoJSON are also used for coordinate encoding in e.g. IIIF, so it would make sense to consider whether the `<geometry>` element should be integrated into the `<facsimile>` system as well.


### Agenda
* Meeting schedule? (Postpone until GR?)
    * JT to send out new poll -- try for after 8:30 
* Repos and organization
    * Use this document as a rolling minutes
* Look through charge: https://tei-c.org/activities/workgroups/gis-charge/
* Look at / read through https://github.com/TEIC/TEI/issues/1474
    * C.f. definition: 
    > `<geo>` (geographical coordinates) contains any expression of a set of geographic coordinates, representing a point, line, or area on the surface of the earth in some notation
* Next steps
    * Ask TEI-L for information
        * Form? Survey?
        * Questions:
            * What are people doing? What are they doing with their TEI files? What would they like to be able to do?
            * Are there any changes that they couldn't live with? 
            * Does it need to be backwards compatible? 
            * Do you use `<geo>` as an inline element? 
            * Do you use `<geoDecl>`?
``` xml
<p>Valparaiso, Chile is located at 
<geo>33 degrees south latitude 
    and 71 degrees west longitude</geo>.</p>
```

 * Tending toward a more permissive approach in P5 with some ideas for more nuanced approach in P6
 * It would be good to be able to check for things like e.g. well-formedness
 * Question of granularity: is `<geo>` equivalent to `geometry` or should it be able to hold the entire feature collection
 * Think about following guidelines from [ISO 6709](https://en.wikipedia.org/wiki/ISO_6709)
 * Should we just create a new element `<geometry>`, leaving `<geo>` in for now?
 * What are the different kind of coordinate spaces that would need to be specified for a generic `<geometry>`? 

