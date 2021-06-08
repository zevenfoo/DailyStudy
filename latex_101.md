# LaTeX 101

## How to Compile?

LaTeX is a multiple pass system. Usually, one can use `latexmk` to compile .tex files (to see more information, type `texdoc latexmk` in the command line).

A typical compiling command

```powershell
latexmk -pvc  # preview continuously
        -xelatex  # use xelatex engine
        -cd -outdir=out  # relative path
        <FILE>  # file without a suffix

latexmk -c  # clean aux files
        -cd -outdir=out  # relative path
```

## How to Use CJK characters?

```latex
% use xelatex to compile
\usepackage{ctex}
```
