# CI worker for the OpenCS ontology

The recommended way to use this is via the provided Docker image. Just run:
`docker run -it --rm ghcr.io/opencs-ontology/ci-worker:main python <script name.py> <args>`

If you need an absolute path to the script, then just use `/app/<script name.py>`.

## Scripts
- `split_concepts.py` – processes an RDF dump of the core ontology, splits it into individual concept files, and formats them nicely. Args:
  - input file
  - output dir (no trailing slash)
  - whether to fix DBpedia IRIs (0/1) – use when importing broken MAKG dumps
- `to_mediawiki.py` – converts Turtle files for concepts (as generated by the `split_concepts.py` script) into wikitext to be imported into the OpenCS wiki. Args:
  - input dir (no trailing slash)
  - output dir (no trailing slash)
- `package.py` – packages the ontology's files for release. Args:
  - input dir – the root of the OpenCS repo (no trailing slash)
  - output dir (no trailing slash)
  - version tag (semver) for the main ontology – the schema is versioned manually in it Turtle file
- `generate_pages.py` – generates files from templates for GitHub Pages. Args:
  - current release - version tag for the main ontology
  - repository name - name of the origin repository
  - output path - output directory path
- `validate.py` – validates the ontology using SHACL. Args:
  - input dir – the root of the OpenCS
