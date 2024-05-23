## Prerequisites

This workshop uses GPT-4 language models via the OpenAI API. This requires an OpenAI API key. Signup requires establishing a payment method, but the cost should be minimal (i.e., less than $10 even with heavy repetition and playing around).

1. Create (or sign into) an [OpenAI Developer account](https://platform.openai.com/signup)
2. Create an [API Key](https://platform.openai.com/account/api-keys)
3. Create a file called `.env` that contains:
   ```
   OPENAI_API_KEY=[YOUR API KEY]
   ```

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
docker compose --env-file=.local-env --env-file=.env up
```

