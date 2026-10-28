# formatter

An EL program that pretty-prints JSON or XML from standard input, choosing the
format from the content: input whose first non-blank character is `<` is XML,
anything else is decoded as JSON. Output uses two-space indentation.

```sh
el build
echo '{"name":"EL","values":[1,true,null]}' | el run
echo '<cfg a="1"><k>v</k><e/></cfg>' | el run
```

Malformed or empty input, and input that is not valid UTF-8, is reported on
standard error and the program exits with status 1.

XML elements that contain non-blank text keep their content on one line so the
text is never altered; element-only content gets one child per line.

Run the tests with `el test`. This needs an EL compiler with the `Json` and
`Xml` prelude modules.
