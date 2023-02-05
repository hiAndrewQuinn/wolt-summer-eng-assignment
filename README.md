# Wolt Summer Eng Assignment

[![PyPI](https://img.shields.io/pypi/v/wolt-summer-eng-assignment.svg)][pypi_]
[![Status](https://img.shields.io/pypi/status/wolt-summer-eng-assignment.svg)][status]
[![Python Version](https://img.shields.io/pypi/pyversions/wolt-summer-eng-assignment)][python version]
[![License](https://img.shields.io/pypi/l/wolt-summer-eng-assignment)][license]

[![Read the documentation at https://wolt-summer-eng-assignment.readthedocs.io/](https://img.shields.io/readthedocs/wolt-summer-eng-assignment/latest.svg?label=Read%20the%20Docs)][read the docs]
[![Tests](https://github.com/hiAndrewQuinn/wolt-summer-eng-assignment/workflows/Tests/badge.svg)][tests]
[![Codecov](https://codecov.io/gh/hiAndrewQuinn/wolt-summer-eng-assignment/branch/main/graph/badge.svg)][codecov]

[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)][pre-commit]
[![Black](https://img.shields.io/badge/code%20style-black-000000.svg)][black]

[pypi_]: https://pypi.org/project/wolt-summer-eng-assignment/
[status]: https://pypi.org/project/wolt-summer-eng-assignment/
[python version]: https://pypi.org/project/wolt-summer-eng-assignment
[read the docs]: https://wolt-summer-eng-assignment.readthedocs.io/
[tests]: https://github.com/hiAndrewQuinn/wolt-summer-eng-assignment/actions?workflow=Tests
[codecov]: https://app.codecov.io/gh/hiAndrewQuinn/wolt-summer-eng-assignment
[pre-commit]: https://github.com/pre-commit/pre-commit
[black]: https://github.com/psf/black

Hi! I'm Andrew, and this is my attempt at the [Python backend preliminary coding assignment](https://github.com/woltapp/engineering-summer-intern-2023) for Wolt. I like animated screenshots, so here's an example of my solution in action:

![Demo with 4 multiplexed screens of code. Upper left shows the web server running; lower left shows the content of a request payload I'm sending with a simple Bash script. Lower right shows a 2 second loop of the response payload of the lower right, which I change in real time. Upper right shows the results of the pytest and miscellaneous information.](https://user-images.githubusercontent.com/53230903/216786616-c4c7be95-0f5d-4ea2-8ef8-aad03fc6a60b.svg)

(You can see an identical SVG in the `demo.svg` of this file as well, although generally speaking I don't like committing large files like that to repos.)

# Quickstart

## Using Poetry (recommended)

First install [Poetry](https://python-poetry.org/docs/) however you wish. Then run

```python
poetry install
poetry run wolt-summer-eng-assignment --help
```

Then go ahead and send your payloads to whatever port it assigns you, most likely `localhost:8000`. Among other things Poetry also makes it easy to run the code tests for yourself by using `poetry run pytest` or `nox`.

## Using `pip`

First ensure your system has the required dependencies, by running

```bash
pip install -r requirements.txt
```

in the root directory. Then simply enter the `src` folder and run as a module:

```bash
cd src/
python -m wolt_summer_eng_assignment
```

You should now be able to send your request payloads however you wish to `localhost`.

## Sending payload packets easily with `payload-example.sh`

I have included a copy of the `example.sh` script from
the animated SVG above in the
root directory of this project as `payload-example.sh` to
make things as easy as possible to debug.

With the server running in one terminal, and assuming
it has mapped to `localhost:8000`, simply run

```bash
bash payload-example.sh
```

to send a payload JSON to the server. It will print the
response payload JSON in turn. You can run this every
2 seconds as you dynamically play around with the variables
by running

```bash
watch 'bash payload-example.sh'
```

in a separate terminal as well. 

## For code review

There are a lot of files in here, I know. Here are the ones you _actually_ want to look at:


```bash
.
├── src
│   └── wolt_summer_eng_assignment
│       ├── logic.py
│       ├── __main__.py
└── tests
    ├── test_logic.py
    └── test_main.py
```

- `__main__.py` contains the FastAPI wrapper that we run in a loop to create the server.
- `logic.py` contains the data models and business logic of the application.
  - These _used_ to be in `__main__.py` as well, but I figured splitting them into their
    own file made it easier to keep track of everything.
- `test_logic.py` is where I implement the unit tests for `logic.py`. These were incredibly helpful to write!
- `test_main.py` is where I _would_ put the code to test the server part, but I decided against it due to time constraints.


## Features

This is just a preliminary assignment, but here are some directions I could go.

- *Figure out a way to test the server code in `__main__.py`.* I factored out the business logic to `logic.py` and
  have that tested fairly well (writing those unit tests actually showed me a lot of flaws in my original thinking),
  but I don't have anything in place testing the FastAPI code itself yet. I'm not doing anything fancy with it but
  it would be nice.
- *Fix everything `nox` complains about.* I do `poetry run pytest` in the animated SVG but that's actually just the
  tip of the iceberg. You can run `nox` on this repo to see _a lot_ more places where things can be fixed,
  dependency patches could be applied, etc.
- *Use types!* `mypy` exists in here and would probably make this look much more professional if I were to use it.

## Requirements

All documented in [Wolt's "Specifications" section](https://github.com/woltapp/engineering-summer-intern-2023#specification).

## Credits

This project was generated from [@cjolowicz]'s [Hypermodern Python Cookiecutter] template.

[@cjolowicz]: https://github.com/cjolowicz
[pypi]: https://pypi.org/
[hypermodern python cookiecutter]: https://github.com/cjolowicz/cookiecutter-hypermodern-python
[file an issue]: https://github.com/hiAndrewQuinn/wolt-summer-eng-assignment/issues
[pip]: https://pip.pypa.io/

<!-- github-only -->

[license]: https://github.com/hiAndrewQuinn/wolt-summer-eng-assignment/blob/main/LICENSE
[contributor guide]: https://github.com/hiAndrewQuinn/wolt-summer-eng-assignment/blob/main/CONTRIBUTING.md
[command-line reference]: https://wolt-summer-eng-assignment.readthedocs.io/en/latest/usage.html
