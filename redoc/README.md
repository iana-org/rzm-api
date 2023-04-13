# Overview 

## Redoc tool
Redoc is an open-source tool for generating documentation from OpenAPI (fka Swagger) definitions. Redoc is the 
community version of Redocly API documentation tool.

* https://github.com/Redocly/redoc 
* https://redocly.com/redoc
* https://redocly.com/docs/redoc/deployment/intro

##  Redocly CLI

Redocly CLI (fka OpenAPI CLI) toolbox with rich validation and bundling features.

* https://github.com/Redocly/redocly-cli
* https://redocly.com/docs/cli/commands/build-docs/
* https://redocly.com/docs/cli/
* https://redocly.com/redocly-cli

## Build documentation 

- Install Redocly CLI (https://redocly.com/docs/redoc/deployment/cli/)
  ```
  docker pull redocly/cli
  ``` 
  
- Clone this repo and go to redoc folder
  ```
  git clone git@github.com:iana-org/rzm-api.git
  cd redoc
  ```
- Get the latest copy of tld-manager.json and put it in redoc folder
  ```
  https://github.com/iana-internal/rzms/blob/master/tld-manager-api/openapi/src/main/resources/tld-manager.json
  ``` 
- Validate specification file and update if needed.
  ```
  docker run --rm -v $PWD:/spec redocly/cli lint tld-manager.json
  ```
- Bundle all specification files into a single yaml file
  ```
  docker run --rm -v $PWD:/spec redocly/cli bundle tld-manager.json --output=tld-manager.yaml
  ```
- Update template.hbs if needed.
- Generate HTML-file
```
docker run --rm \
  -v $PWD:/spec \
  redocly/cli build-docs \
  tld-manager.yaml \
  --template=template.hbs \
  --output=index.html
```
- Review index.html
  ```
  open index.html
  ```

## Publish documentation 

- Move index.html file to ./docs
```
mv index.html ../docs
```
- Push the latest index.html to GitHub

