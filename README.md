# document-builder GitHub Action

GitHub Action for building LaTeX and Markdown documents using a Makefile.

## Base image

The Docker image is built based on the configuration in `document-builder/` and it is deployed on [`Docker Hub`](https://hub.docker.com/r/ldbc/document-builder).

To build the image, navigate to the `document-builder/` directory.

```bash
cd document-builder
docker build --tag ldbc/document-builder:2021 .
docker tag ldbc/document-builder:2021 ldbc/document-builder:latest
```

To deploy the image on Docker Hub, run:

```bash
docker push ldbc/document-builder:2021
docker push ldbc/document-builder:latest
```

## Local usage

To use this Docker image, create a `Makefile` that performs the required build steps. Then, test the image as follows;

```bash
docker run --rm -v `pwd`:"/github/workspace" ldbc/document-builder [arguments]
```

The `[arguments]` are optional and are passed to the Makefile.

## Usage with GitHub Actions

Create a `.yml` workflow file in your repository under `.github/workflows/`.
For example, to run `make ci`, use the following configuration:

```yaml
jobs:
  job_name:
    runs-on: ...
    name: ...
    steps:
    - name: Build PDFs with the LaTeX engine in Docker
      uses: ldbc/document-builder-actions@main
      with:
        makefile-arguments: ci
```
