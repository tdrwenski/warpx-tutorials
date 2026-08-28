# WarpX tutorial container

A Docker image that serves the WarpX tutorials as a browser-based **JupyterLab**
session: notebooks, a terminal, and a ready-to-use `warpx` conda environment.

## Run it locally

```bash
docker build -f containers/tutorial/Dockerfile -t warpx-tutorial:local .
docker run --rm -p 3000:3000 warpx-tutorial:local
```

Open <http://localhost:3000/lab>, launch a **Terminal**, and run:

```bash
cd ~/warpx-tutorials/episodes/files
warpx.1d input_1d_two_stream_instability.txt
```

then open `files/analysis_1d_twostream.ipynb` to visualize the results.

## Automated builds

`.github/workflows/tutorial-docker-image.yml` builds the image and, on `main`,
pushes it to `ghcr.io/blast-warpx/warpx-tutorials/tutorial:latest` (plus a
`:sha-<commit>` tag). The AWS deployment pulls that image.
