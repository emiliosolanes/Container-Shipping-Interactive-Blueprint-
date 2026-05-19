# DCSA Industry Blueprint — Interactive Explorer
A side project by Emilio Solanes to show what becomes possible when standards are open.
Not intended to be maintained. Built it because I wanted to see what could be done. 

# What it is
A single HTML file. No server, no install, no login. Open it in a browser and it works.
It covers all 31 BPMN process diagrams across the three container shipping journeys — Shipment, Equipment, and Vessel — and links each process to its corresponding DCSA API specification and Track & Trace events.

# What you can explore

BPMN diagrams: all process models rendered interactively, with pan and zoom
API specifications: endpoints, parameters, and request/response fields from the DCSA OpenAPI specs
Track & Trace events: the approx 300 TNT events mapped to the processes that generate them
Process descriptions: the full text from the DCSA reference documentation

# How to use it
Open dcsa-blueprint-v3.html in any modern browser (Chrome, Edge, Firefox, Safari). That's it.
Built on open standards
Everything in this tool comes from publicly available DCSA material — the Blueprint ZIP, the OpenAPI YAML specifications, and the TNT events catalog. All free to use and build on.
This is the point: open standards are infrastructure. The more people explore, understand, and build on them, the more valuable they become.

# Links

DCSA Industry Blueprint: https://reference.dcsa.org/content/standards/industry-blueprint/v2026-q1/industry-blueprint-2026-q1
DCSA Open Standards: https://app.swaggerhub.com/apis/dcsaorg/
DCSA References Portal: https://reference.dcsa.org/

# How it was built
Coding assistant + the source material is all public:

The DCSA Industry Blueprint ZIP (from reference.dcsa.org) — contains 33 BPMN XML files
The DCSA OpenAPI YAML specifications (from dcsa.org/standards)
The TNT events combinations spreadsheet

The BPMN files are parsed in Python, stripped down to just the rendering data (element types, positions, colors, connections), compressed with gzip, and embedded as base64 inside the HTML. 
The browser decompresses it at load time using the native DecompressionStream API, no libraries needed. Same approach for the API specs and events.
A custom SVG renderer draws the diagrams from the extracted data. 
Everything else, navigation, search, tabs, pan and zoom is vanilla HTML, CSS, and JavaScript.
No framework. No build step. No dependencies.


