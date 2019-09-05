SHELL:=/bin/bash
ROOT_DIR:=$(shell dirname $(realpath $(lastword $(MAKEFILE_LIST))))
APP_NAME:=app
PYTHON:=python3

all: dependencies

test_env: dependencies

venv:
	if [ ! -d $(ROOT_DIR)/env ]; then $(PYTHON) -m venv $(ROOT_DIR)/env; fi

dependencies: venv
	source $(ROOT_DIR)/env/bin/activate && \
	python -m pip install -r $(ROOT_DIR)/../../requirements.txt && \
	python -m pip install -r $(ROOT_DIR)/requirements_pynamodb.txt && \
	python -m pip install -e ../..

clean_testenv:
	rm -rf $(ROOT_DIR)/env;
	rm -rf $(ROOT_DIR)/$(APP_NAME)/*.pyc;