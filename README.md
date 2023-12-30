# BadLaTeX!!
BadApple!! [played in LaTeX](https://www.youtube.com/watch?v=RYrw_swOD-U). Using tikz pictures.

---

## The process
### Extracting frames
```
ffmpeg -ss 00:01 -i ~/Wideo/BadApple\!\!.mp4 /tmp/badapple/frame%04d.bmp
```

### Conversion to `svg`
Using [potrace](https://potrace.sourceforge.net/).
```
for frame in /tmp/badapple/*; do
    echo $frame
    potrace -b svg $frame -o /tmp/badsvg/$(basename $frame).svg
done
```

### Conversion to `tikz` code
Using [svg2tikz](http://xyz2tex.github.io/svg2tikz/).
```
for frame in /tmp/badsvg/*; do
    echo $frame
    svg2tikz --figonly $frame | tail -n +5 > /tmp/badtikz/$(basename $frame).tex
done
```

### Compiling `pdf`
```
pdflatex prezka.tex
```

---

All code included, you can compile presentation yourself.
It may take several minutes tho
