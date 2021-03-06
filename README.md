# Pandoc PlantUML Filter (Fork with built filter)

Replaces `CodeBlocks` with `plantuml` class with PlantUML generated UML diagram

***Note: This fork contains extended instructions and a built filter so you won't need a full haskell/cabal installation to use this.***

## Requirements

- `plantuml` in `PATH` which launches PlantUML jar (see `scripts` folder)
- `pandoc`
- the plantuml filter is built and included in the root of this fork!

## Build From Source (OSX)

This fork has the built filder so you don't need to build but if you'd like to here are the steps (OSX)

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
