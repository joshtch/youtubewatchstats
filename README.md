# youtubewatchstats
YouTube Watch History Statistics App

## Getting Started

Requirements:

 - a Google account to access the YouTube API;
 - a \*nix shell, and
 - Python 3 with `pip` installed.
 - **Optional**: `virtualenv` if you want to install dependencies locally.

### Step 1: Obtain YouTube Data API Key

First you'll need to get obtain authorization credentials for the YouTube Data
API v3.

Go to the [Google Developers
Console](https://console.developers.google.com/). Log in if necessary.

Then in the YouTube Data API dashboard (search for it or just [click
here](https://console.developers.google.com/apis/library/youtube.googleapis.com)),
make sure you've enabled the API, and if not, do that.

Then go to the YouTube Data API Credentials page (or [click
here](https://console.developers.google.com/apis/api/youtube.googleapis.com/credentials)),
and select `Create Credentials`, then `API Key`. It should display your API
Key, which you will need for the next step. Make sure you copy it somewhere,
like your clipboard.

### Step 2: Set up the environment

In the shell, run this command, with the API key you obtained in the previous step in place of
`<YOUR_API_Key>`  in the
command below:

```sh
$ export API_KEYS='["<YOUR_API_KEY>"]'
```

_(**Important**: note the `S` in `API_KEYS`, and the `'["`/`"]'` characters around the key.)_

Next, clone the repo:

```sh
$ git clone --depth 1 https://github.com/marckhoury/youtubewatchstats youtubewatchstats && cd $_
```

### Step 2a (optional): Set up a virtual environment

Set up a virtual environment to install your dependencies to:

```sh
$ virtualenv .venv
```

And now activate it:

```sh
$ . ./.venv/bin/activate
```

Remember to run `deactivate` or close the shell when you're done.

### Step 3: Install the dependencies.

Install required Python packages:

```sh
$ pip install -r requirements.txt
```

<sub>_**Note**: On systems where Python 2 is the default (check with_ `python
--version`_), you may need to specify Python 3 explicitly with_ `pip3 install
-r requirements.txt`; _for `virtualenv`, run_ `pip3 install virtualenv` _to
install `virtualenv` and_ `python3 -m virtualenv .venv` _to set up. In either
case, the rest of the commands should be run exactly as-is._</sub>

### Step 4: Run it!

Start the `gunicorn` server:

```sh
$ DATABASE_URL='' gunicorn server:app --timeout=300
```

If everything worked as expected, you should be up and running! View the page
in your browser at [http://127.0.0.1:8000/](http://127.0.0.1:8000/).
