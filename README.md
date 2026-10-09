# Apache Sling Shared GitHub Actions

## Usage

Create GitHub workflow in project file:

```
.github/workflows/main-build.yml
```

 with content:

```yaml
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#       http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.

name: Verify

on:
  push:
  pull_request:

jobs:
  build:
    name: Verify
    uses: apache/sling-github-tooling/.github/workflows/main-build@v1

```

## Configuration

The [Sling module descriptor](https://cwiki.apache.org/confluence/display/SLING/Sling+module+descriptor) with name `.sling-module.json` is evaluated and used for parameterizing the build.

## Versioning

The workflows maintained here follow semantic versioning, however this requires some thought when releasing (<https://devopsjournal.io/blog/2022/10/19/How-GitHub-Actions-versioning-works>) as this requires tags not being immutable and multiple tags potentially pointing to the same version.
The notation `uses: <apache/sling-tooling-github/>.github/workflows/main-build.yml@<ref>` allows the following values for refs:

1. SHA1 commit ids
1. Tag Names
1. Branch Names (same tag name takes precedence)

# References

1. [Workflow Syntax](https://docs.github.com/en/actions/writing-workflows/workflow-syntax-for-github-actions)
1. [Reusing Workflows](https://docs.github.com/en/actions/sharing-automations/reusing-workflows)
1. [Maven Shared GitHub Actions](https://github.com/apache/maven-gh-actions-shared)
