# Pandoc PlantUML Filter

[![Travis build status](https://travis-ci.org/kbonne/pandoc-plantuml-filter.png?branch=master)](https://travis-ci.org/kbonne/pandoc-plantuml-filter)


Replaces `CodeBlocks` with `plantuml` class with PlantUML generated UML diagram

**This is a work in progress.**

## Requirements

- `plantuml` in `PATH` which launches PlantUML jar (see `scripts` folder)
- `pandoc`
- `cabal` 

## Installation (OSX)

Prerequisites:

- brew install graphviz 
- brew install plantuml
- brew install cabal-install
- cabal update
- cabal install cabal-install

Checkout the source. Change into the folder. Then run:
- cabal install

This will generate the filter here: 
./dist/build/pandoc-plantuml-filter/pandoc-plantuml-filter

You'll need to also place plantuml.jar into /opt/plantuml/plantuml.jar 
And then place plantuml in the path

## Usage

e.g. Generating .pdf from this file
```
pandoc README.md --variable=geometry:a4paper,margin=2cm --variable=fontsize:11pt -o README.pdf --filter ./dist/build/pandoc-plantuml-filter/pandoc-plantuml-filter
```

## Tests

### Javascript

Should be skipped

```javascript
var s = "JavaScript syntax highlighting";
alert(s);
```

### PlantUML

Should be processed!

```plantuml
@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
@enduml
```

This one as well

```{.plantuml include="README.md"}
@startuml
class Car

Driver - Car : drives >
Car *- Wheel : have 4 >
Car -- Person : < owns

@enduml
