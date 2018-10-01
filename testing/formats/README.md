# Testing import of images

## Mac

### Without librsvg

Seems that importing pdf and generating pdf:

```bash
$ dot -Tpdf test_pdf.dot > test_pdf.pdf
Warning: No loadimage plugin for "pdf:cairo"
```

fails whereas importing svg and generating svg works:

```bash
$ dot -Tsvg test_svg.dot > test_svg.svg
```

<img src="test_svg.svg" width="200">

That leaves image refs in the generated .svg rather than embedding. 

W/o librsvg, using `-Tsvg:cairo` doesn't work:

```bash
$ dot -Tsvg:cairo test_svg.dot > test_svg-cairo.svg
Warning: No loadimage plugin for "svg:cairo"
```

Importing png and generating png works:

```bash
dot -Tpng test_png.dot > test_png.png
```

<img src="test_png.png" width="200">


### With librsvg

```bash
$ brew reinstall graphviz --with-librsvg --with-app --with-pango
```

then this works again:

```bash
dot -Tsvg:cairo test_svg.dot > test_svg-cairo.svg
```

<img src="test_svg-cairo.svg" width="200">

Important: this embeds the images instead of leaving refs to other files.
