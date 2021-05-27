# saxon-js bug reproduction

This repository contains a minimal reproduction of a transformation that fails with `saxon-js`, but succeeds with `SaxonHE 10.2`.

Note that this failure appears to have been introduced with `v2.1.0`; however, I do not see an obvious source of the change in the [change log](https://www.saxonica.com/saxon-js/release-notes.xml#2.1).

The notable quality of the transformation is that it is XSLT 1.0, and imports an XSLT 2.0 stylesheet with an `xsl:output` element.

To reproduce, run:

```bash
npx xslt3 -s:./source.sch -xsl:transform.xsl -o:./output.xsl
# or
npm run transform
```

This will produce the error:

```
Transformation failure: Error SESU0013
    Serializer does not support the requested XML version: 2.0
Error SESU0013
    Serializer does not support the requested XML version: 2.0
npm ERR! code 2
npm ERR! path /Users/dan/src/xslt3-import-bug-repro
npm ERR! command failed
npm ERR! command sh -c xslt3 -s:./source.sch -xsl:transform.xsl -o:./output.xsl
```
