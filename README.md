# new-relic-orb
Orb for recording deployment on New Relic.

## View in the orb registry
See the [new-relic in the registry](https://circleci.com/orbs/registry/orb/tiendanube/new-relic)
for the full details of jobs, commands, and executors available in this orb.

## Setup required to use this orb
The following **required** dependencies must be configured in CircleCI in order to use this orb:
* NEW_RELIC_APP_ID - Application Id
* NEW_RELIC_API_KEY - Api Key

## Sample use in CircleCI config.yml

```yaml
version: 2.1

orbs:
  new-relic: tiendanube/new-relic@1.0.0

jobs:
  build:
    docker:
      - image: circleci/openjdk:8-jdk
    steps:
      - checkout
      - new-relic/record-deployment:
          app-id: ${NEW_RELIC_APP_ID}
          api-key: ${NEW_RELIC_API_KEY}
          revision: ${CIRCLE_SHA1:0:7}
          user: ${CIRCLE_USERNAME}
```
