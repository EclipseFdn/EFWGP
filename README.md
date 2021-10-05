<!--
 * Copyright (C) 2008,2021 Eclipse Foundation and others. 
 * 
 * This program and the accompanying materials are made available under the
 * terms of the Eclipse Public License v. 2.0 which is available at
 * http://www.eclipse.org/legal/epl-2.0.
 * 
 * SPDX-FileType: DOCUMENTATION
 *
 * SPDX-License-Identifier: EPL-2.0
-->

[![REUSE status](https://api.reuse.software/badge/github.com/EclipseFdn/EFWGP)](https://api.reuse.software/info/github.com/EclipseFdn/EFWGP)

# Eclipse Foundation Working Groups

This repository contains the documents that define the Eclipse Foundation Working Group Process.

* source/process.adoc - The Eclipse Foundation Working Group Process document
* source/operations.adoc - The companion operations guide.

Changes to the process document require approval from the Eclipse Foundation's board of directors. The operations document can (and will) be updated as necessary.

These documents are published on the [Eclipse Foundation's Working Groups website](https://www.eclipse.org/org/workinggroups/about.php).

## Build

This project has a Maven-based build that uses AsciidoctorJ to compile sources into HTML.

    > mvn clean generate-resources
    
## Converting

For ease of editing, we use Google Docs to edit the content. When it's time to publish, we download the document as webpage and use this command to turn it into AsciiDoc (and yes, it feels a bit dirty):

````
$ tidy  -gdoc --hide-comments yes EclipseFoundationWorkingGroupOperationsGuide2.html | sed -E -e 's/https:\/\/www\.google\.com\/url\?q=([^%[&]+)(%23([^&]+))?\&[^["]+/\1#\3/g' | pandoc --atx-headers --wrap=none -f html -t asciidoc > operations.adoc
````

## Other

Eclipse and the Eclipse Logo are registered trademarks of the Eclipse Foundation, Inc.

Copyright &copy; The Eclipse Foundation. Distributed under the terms of the Eclipse Public License 2.0.