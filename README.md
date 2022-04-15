# Github Action for LaTeX / TeXtool

Compiles a TeXtool project inside a Github Actions pipline.

## Usage

You need to add a docker setup action first.
Specific the `path` and the action will compile your tex files.
It outputs a `pdf` variable with the path to the rendered pdf file.

Internal, latexmk is used, and sometimes it doesn't detect all references correct.
If so, simply add the action twice.
## Example
```yaml
steps:
  - uses: actions/checkout@v3

  - id: setup-docker
    name: Set up Docker Buildx
    uses: docker/setup-buildx-action@v1
    
  - id: latex
    uses: alexander-lindner/latex-action@v1.4
    with:
      path: 'thesis'

  - name: pdf path
    run: echo ${{ steps.latex.outputs.pdf }}
    shell: bash
```