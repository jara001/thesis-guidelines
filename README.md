# Thesis Guidelines
_A Work-in-Progress set of instructions and hints for writing (better) theses at CTU._

For sake of brevity, we target only LaTeX format. If you are brave enough to write your thesis in, e.g., Word... I wish you luck. But these instructions should be also helpful.

Very good sources are also presentations from IMR [here](https://imr.ciirc.cvut.cz/uploads/Education/jak_napsat_BP.pdf) and [here](https://imr.ciirc.cvut.cz/uploads/Education/jak_prezentovat.pdf) (both Czech only).


**Table of Contents**
- [Template](#template)
- [Text typeset](#text-typeset)
- [Equations](#equations)
- [Figures](#figures)
- [References](#references)
- [Citations](#citations)


## tl;dr

These are only hints. You should at least stick to:

- **Be consistent.** = No matter which style you use, use it consistenly.
- **Be clear.** = Re-read your sentences. Avoid complicated wording.
- _TODO: Add more._


## Template

There are two basic templates for the thesis:
- [ctuthesis](https://github.com/tohecz/ctuthesis)
  - Remove line `\setlength{\parskip}{5ex plus 0.2ex minus 0.2ex}` to get rid of large vertical spaces.
  - Remote `preprint = \ctuverlog` to get rid of git hash from each page.
- [ctustyle](http://petr.olsak.net/ctustyle-e.html)


For writing the LaTeX documents I personally use [latexextra.tex](https://github.com/jara001/latexextra.tex). Some parts of that are placed here. You can use it as a reference for 'how to do stuff slightly differently'.


## Text typeset

1. Be consistent. It is helpful to set your own macros for various names to avoid using different capitalization:
```latex
\usepackage{xspace}
\newcommand{\MyCustomName}{Very CoOl WeirdLY capitalZed name\xspace}
```
_Note: The `\xspace` is replaced with a space only when it is necessary, therefore you do not have to use `\MyCustomName{}`, but `\MyCustomName`. The first variant ensures that there will be no space in any condition._

_Another note: `xspace` might act weirdly. But it has never happened to me._

2. Use non-breaking spaces in the names, where necessary. For example, if you want to talk about second Starcraft, use `Stacraft~II`.
3. Quotation marks are **NOT** done using `"`. That is a symbol for inch.
  - English quotation marks are: **``** before text and **''** after the text. Note, that the second one is two times **'**. Differences can be seen [here](https://www.maths.tcd.ie/~dwilkins/LaTeXPrimer/QuotDash.html).
  - Czech quotation marks are done using `\uv{}`. This requires `\usepackage[czech]{babel}` or `\usepackage{cslatex}`.
4. Writing a list of items in better done as an enumerated one as it looks slightly better:
_...and we used multiple approaches: (i) Follow The Gap, (ii) Pure Pursuit, and (iii) some other cool technique._

You can use environment [`inlinelist`](https://github.com/jara001/latexextra.tex/blob/d3b877b06cade6557256f2435566307028b262bd/latexextra.tex#L191-L212) to do this:
```latex
and we used multiple approaches:
\begin{inlinelist}
    \item Follow The Gap,
    \item Pure Pursuit, and
    \item some other cool technique.
\end{inlinelist}%
```
_Note: End `%` ensures that there will be no linebreak._
5. If you want to split a sentence, or add some breathing room into it, use `--` (long dash) or `;` (semicolon).
6. Units: there are two ways: (i) use `siunitx` package, or (ii) typeset it manually using: `$0.5\,\text{m}$`.
_Note: `\,` is a half space._

## Equations

1. Equations are (generally) not cited in themselves. It is better to cite them beforehand, e.g., `The Newton's first law is [1]:`.
2. To improve readability, don't hesitate to use dot product symbol. It is written as `\cdot`.
3. You can use custom macros in the equations as well. If you want to use it inside and outside of the equation, do this: `\newcommand{\MyVariable}{\ensuremath{V}\xspace}`. It will surround the variable with math environment if necessary.
4. Equations are part of a sentence. They usually contains commas `,` or dots `.` at the end of the sentence.
5. The line above means that there is no reason to indent next line after the equation. Use `\noindent` afterwards.


## Figures

1. Figure captions are sentences. So they end with a period.
2. The command `\caption` can also handle an optional argument. That is used in the list of figures. Use it when the captions itself is too long, contains references, etc. This short caption should not end with a period.
3. When referencing a figure, use `in Figure` not `on`.


## References

1. Use `cleverref`. It will accompany each reference with its type (e.g., Figure). When the reference starts the sentence, use `\Cref{}`, otherwise use `\cref{}`; `Figure 1` x `Fig. 1`.
_Note: Import `cleverref` this way: `\usepackage[capitalise]{cleveref}`._


## Citations

1. Every `\cite` has to be accompanied with a non-breaking space `~` to avoid putting the reference number on a next line; e.g., `in~\cite{cool-paper}`.
2. If you want to cite more papers at once, use them in one command; don't do `\cite{one-paper} \cite{second-paper}`, but `\cite{one-paper,second-paper}`. It will also change the way it is set; `[1] [2]` vs. `[1, 2]`.
