# About the project

This is a blog project.

# Quick start

## Install virtualenv and requirements

On ubuntu:

    apt-get install python-pip
    apt-get install python-virtualenv
    virtuanenv -p python3 .venv
    source .venv/bin/activate
    pip install -r requirements.txt

## Build html pages

In virtual environment:

    make html

## Test html

    make devserver [PORT=8000]

# License

CC0 1.0 Universal
