#  bonsai decision support deployment

This repository provides an example of a decision support deployment interface to a bonsai brain. The deployment interface connects to an exported brain and runs in a web browser.

- Supports *numbers* (float, int, boolean) type states and action only (TODO: extend sample to other types such strings, images)

🚩 Disclaimer: This is not an official Microsoft product. This application is considered an experimental addition to Microsoft Project Bonsai's software toolchain. It's primary goal is to reduce barriers of entry to use Project Bonsai's core Machine Teaching. Pull requests for fixes and small enhancements are welcome, but we do expect this to be replaced by out-of-the-box features of Project Bonsai in the near future.

## Pre-requisites

- Install python packages `pip install -r requirements.txt`
- An exported brain running (see [preview.bons.ai](preview.bons.ai)) and reachable via http requests at  `<exported-brain-url>`. For example below is the docker command for running an exported brain locally, reachable at `<exported-brain-url> = http://localhost:<port>`
    ```bash
    docker run -d -p <port>:5000 <acr_name>.azurecr.io/<workspace-id>/<brain-name>:1-linux-amd64
    ```

## Usage

1. Have an exported brain running and reachable at `<exported-brain-url>`.  
 **Note:** if no `<exported-brain-url>` is passed as an argument, the default exported-brain-url will be assume reachable at `http://localhost:5000`

    `streamlit run launch_decision_support.py <exported-brain-url>`

The application will launch http://localhost:8501/ using your default browser.  The default port can be overridden by specifying `--server.port <port>`, e.g. `streamlit run launch_decision_support.py --server.port 8420`

2. If you want to stop all running docker containers `docker stop $(docker ps -aq)`
