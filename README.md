Introduction
============

The files in this repository show output of testing a docbook to POD conversion pipeline. It uses the reference document:

[http://docbook.org/docs/howto/2009-06-16/howto.xml](#???)

available as HTML via:

[http://docbook.org/docs/howto/2009-06-16/](#???)

The XML piped through the following conversion:

    pandoc -f docbook -t markdown_github > howto.md
    markdown2pod --dialect Theory howto.md > howto_m2pod-patched.pod

The following versions of apps/modules are used:

[pandoc](http://johnmacfarlane.net/pandoc/) 1.13.2

[Markdent](http://search.cpan.org/dist/Markdent/) 0.25 + patches from <https://github.com/aspeer/Markdent>

[Markdown::Pod](???) 0.005 + patches from <https://github.com/aspeer/Markdown-Pod>

Markdown::Pod has been patched to allow the --dialect option + to include handlers missing from the original module + as simple Table formatter (Text::Table::Tiny). Markdent has been patched to work with GitHub markup produced by Pandoc v1.12, v1.13

The resulting output has a number of artifacts still being worked through:

-   Pandoc is not converting the "Schema Jungle" table into markdown - it is preserved as XML in the markdown output

-   The "Removed Elements" table is not formatted correctly in the markdown (possibly by pandoc)

-   Replaceable (e.g. docbook "version" ) elements are not interpreted correctly

These are corner cases - for most simple Docbook documents the pipeline works well as a formatter. As an exampled this README was produced in [XMLMind XML Editor](http://www.xmlmind.com/xmleditor/) using a Docbook 5.0 Section Template and exported to markdown and POD using the above pipeline.
