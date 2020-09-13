# FHIR Implementation Guide Experiment 03
An experimental, externally-template-driven FHIR implementation guide being used as a basis for experimenting with custom ant scripts

## Set up
1. create a folder for a local template, in the root directory; eg `template-local`
1. point the ig.ini file to this template; eg `template = #template-local`

### Local Template
1. Add a file `./package/package.json`
    * following the guidance in the [sample HL7 template](http://build.fhir.org/ig/FHIR/ig-guidance/template.html#changing-the-custom-template)
    * note that a dependency is required in this template to inherit all of the generic template content
1. Add a file `./config.json` with the single entry for the path to the local ant script file
1. Add the actual local ant script file; eg `./scripts/ant-local.xml`

### Local sript file
This is a standard [Apache Ant](https://ant.apache.org/)<sup>TM</sup> script.

See the [manual](https://ant.apache.org/manual/) for full guidance.

In order to make this work, the following changes were made in `ant.local.xml`:
* imported the base template ant script, with `<import file="ant.xml"/>`
* the added target jobs extended the existing targets from the generic templates, using eg `extensionOf="onLoad.extend"`
