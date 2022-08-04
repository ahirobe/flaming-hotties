# Flaming Fuelers Joke Generator!
A quick overview of our NLP Project!

If you have any questions, we probably won't answer them.

This guide covers how our code works and the resources used.

### AI Development and Testing

cd into the `/app` folder

`python3 -m pip install -r requirements.txt`

You'll want to edit line 96 of the `main.py` file to either the URL of the cocalc server you are on or `localhost` if you are running it on your own PC.

From there, run `python3 -m main` to start the server on local, most changes while developing will be picked up in realtime by the server. Note that upon cloning this repository an example project with an untrained model will show up upon running `python3 -m main`.


### Website Development and Deployment

Make sure docker is installed on your system. Look that up if you don't know what that means.

cd into the root directory of the repo then run 

`docker build -t omni .`

once built, run

`docker run -d -p 9000:80 --restart=unless-stopped --name omni omni`

you should then be able to see the `omni` container running when you run 

`docker ps -a`

if it seems to be stuck (i.e. constantly listed as `Restarting`), something is wrong with the docker image or code inside causing it to repeatedly fail.

you can start debugging the project by running 

`docker logs -f omni` 

or

`docker exec -it omni /bin/bash` for an interactive bash terminal (this option only works if the container is running and not stuck in a restart loop)

### Flask(Python) Configuration and Setup

`$'\r': command not found` when attempting to start docker container

this is caused by the the `entrypoint.sh` script somehow having CLRF line endings instead of LF line endings.

to fix this run

`sed -i 's/\r$//' entrypoint.sh`

### How to Use

### Technical Stack

### Datasets

### Model

### Libraries

### About the Team
