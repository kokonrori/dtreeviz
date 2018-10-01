# Testing import of images

Seems that importing pdf and generating pdf:

```bash
$ dot -Tpdf test_pdf.dot > test_pdf.pdf
Warning: No loadimage plugin for "pdf:cairo"
```

fails whereas importing svg and generating svg works:

```bash
$ dot -Tsvg test_svg.dot > test_svg.svg
```

Importing png and generating png works:

```bash
dot -Tpng test_png.dot > test_png.png
```
