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

For ease of editing, we use Google Docs to edit the content. Google Docs, however, does not have any built-in technology for producing reasonable we content, so the output needs to be processed a bit. 

When it's time to publish, we download the document as webpage and use this command to turn it into AsciiDoc (and yes, it feels a bit dirty):

1. Download the Google Doc as a webpage;
2. Convert the HTML into AsciiDoc (the "CLI bit" below);
3. Use an editor to remove the "comments" content at the bottom of the document
4. Use an editor to add a "toc::[]" element under the "version" line.

We'll continue to explore means of improving the automation of the conversion. 

The CLI bit:

````
$ tidy  -gdoc input.html \
| sed -E -e 's/https:\/\/www\.google\.com\/url\?q=([^%[&]+)(%23([^&]+))?\&[^["]+/\1#\3/g' \
| pandoc --atx-headers --wrap=none -f html -t asciidoc \
| grep -v "\[\[h\..*\]\]" > output.adoc
````

1. Clean up the HTML; remove the Gdoc cruft;
2. Strip out the Google "safe" link cruft;
3. Convert from HTML to AsciiDoc; and
4. Remove the Gdoc-generated anchors.

## Other

Eclipse and the Eclipse Logo are registered trademarks of the Eclipse Foundation, Inc.

Copyright &copy; The Eclipse Foundation. Distributed under the terms of the Eclipse Public License 2.0.