# speech to text module

## Prerequisites

* setup google text to speech cloud service account
* save credentials in json file
* set environment var: `export GOOGLE_APPLICATION_CREDENTIALS="/path/to/keyfile.json"`
<<<<<<< HEAD
* install portaudio: `brew install portaudio`
=======
* isnstall portaudio: `brew install portaudio`
>>>>>>> c89341fd9c75561a451b0a966d5504320a76ab92

## Installation

* install pipx on osx: `brew install pipx; pipx ensurepath`
* install pips on raspbian os:
    * uninstall previous version `sudo apt-get remove pipx`
    * install pip: `sudo apt-get install python3-pip python3-venv`
    * then pipx:`python3 -m pip install --user pipx`
    * then `python3 -m pipx ensurepath`
* run `pipx install .`

## Development

* create virtual environment : `python3 -m venv .venv`
* activate `source .venv/bin/activate` (`deactivate` to exit)
* install dependencies `pip install -r requirements.txt`

## Links

* https://medium.com/google-cloud/building-a-web-server-which-receives-a-browser-microphone-stream-and-uses-dialogflow-or-the-speech-62b47499fc71
* https://github.com/googleapis/python-speech/tree/master/samples/snippets
