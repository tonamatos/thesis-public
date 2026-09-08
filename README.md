# On Complexity, Computation, and Graph Homomorphisms

LaTeX sources for my PhD thesis, submitted to the Graduate Department of Mathematics,
University of Toronto, 2026.

**[thesis.wiederhold.dev](https://thesis.wiederhold.dev)** — compiled thesis.

## Abstract

A wide range of problems in computer science, including constraint satisfaction, can be
framed in the language of graph homomorphisms. There are problems for which the existence
of a solution may be proved by means of the Axiom of Choice or a non-principal ultrafilter.
Although such solutions exist abstractly, in practice we want solutions that are definable,
and so it is natural to impose restrictions. Interestingly, this often makes the problems
harder to solve, but the solutions have a concrete description. This thesis studies the cost
of insisting on definable solutions.

Descriptive set theory provides the language for all three substantive chapters: Borel
definability for Chapter 2, the Baire-class hierarchy for Chapter 3, and Polish group
actions for Chapter 4.

## Building

The thesis uses the [`ut-thesis`](https://ctan.org/tex-archive/macros/latex/contrib/ut-thesis/)
document class ([source](https://github.com/jessexknight/ut-thesis)) together with my own
style files, included as a submodule.

`ut-thesis-local.cls` is vendored at the repository root rather than taken from the local TeX
installation. Versions of the class differ in whether they define theorem environments,
which collides with the declarations in `common/tonas-thesis.sty`; pinning the class here
keeps local and CI builds identical. It is renamed rather than shipped as
`ut-thesis.cls` so that no installed copy can shadow it, as the LPPL requires for
modified works.

```
git clone --recurse-submodules https://github.com/tonamatos/thesis-public.git
cd thesis-public
pdflatex thesis.tex && bibtex thesis && pdflatex thesis.tex && pdflatex thesis.tex
```

## Layout

| Path | Contents |
| --- | --- |
| `thesis.tex` | Root document |
| `ut-thesis-local.cls` | Vendored document class, renamed copy of ut-thesis v3.1.8 (LPPL 1.3c) |
| `chapters/` | Chapter sources |
| `figures/` | TikZ figures |
| `images/` | Raster and vector figures |
| `bibliography/` | BibTeX database |
| `common/` | Style files ([tonas-latex](https://github.com/tonamatos/tonas-latex), submodule) |
| `tools/` | Figure-generation scripts |

## Automation

GitHub Actions compiles `thesis.tex` on every push to `main` and deploys the result,
together with the landing page, to the `gh-pages` branch.

## Licence

See [LICENSE](LICENSE).
