## Running Locally

To use a snapshot of the notebooks within the JupyterLab environment without affecting the local repo:

```shell
docker compose build
docker compose up
```

Look for the `http://localhost:8888/lab?token=...` URL in the log.

## Developing Notebooks

To mount the local repo directly into JupyterLab (e.g., for development of notebooks), replace the second command with:

```shell
docker compose --env-file=.local-env up
```

