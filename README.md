# Tangler website

This repository contains the content for [http://www.tangler.io](http://www.tangler.io)

This website is managed through [Punch](http://laktek.github.io/punch/)

## Prerequisites

    npm install punch

## Using punch local server

    node_modules/.bin/punch s
    http://localhost:9009/

## Generating static content

    node_modules/.bin/punch g

## Generating module documentation

Tangler can introspect modules and generate documentation pages for them.
Run the following command to generate the documentation:

    ../Tangler/bin/tangler documentation:generate tanglerdoc.xml

The tanglerdoc.xml contains relative paths to modules. This assumes your core, modules and tangler.github.io repo's are all in the same parent directory.
