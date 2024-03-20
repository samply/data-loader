# Data loader

A Docker image that loads from files into a FHIR store.

The data is loaded by [blazectl](https://github.com/samply/blazectl). The data should be stored in FHIR JSON format in one or more files in a single directory. The directory should be mounted in your Docker container as /app/sample. There are no limitations on data model or profile.

## Quickstart

To build a local image, type the following:

```
docker build -t samply/data-loader . --no-cache
```

The supplied `docker-compose.yml` file can be used for trying things out. It contains a FHIR store (Blaze). Test data is supplied with this repo. Start Docker like this:

```
docker-compose up
```

Wait for the data to finish loading (a couple of minutes). Then try this (in a different console):

```
curl http://localhost:8080/fhir/Patient
```

This should return a list of patients known to the store.

## Configuration

The data loader is configured using environment variables:

| Variable                                  | Description                                                                                                        | Default                          |
|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------|----------------------------------|
| `FHIR_STORE_URL`                          | HTTP Address of the FHIR store                                                                                     | http://store:8080/fhir           |

## Building

```
docker build -t samply/data-loader . --no-cache
```

## License

Copyright 2024 The Samply Community
Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at
http://www.apache.org/licenses/LICENSE-2.0
Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
