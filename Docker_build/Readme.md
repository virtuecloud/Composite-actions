# Docker build action

<h1 align="center"> Virtuecloud </h1> <br>
<p align="center">
  <a href="https://virtuecloud.io/">
    <img alt="Virtuecloud" title="Virtuecloud" src="https://virtuecloud.io/assets/images/VitueCloud_Logo.png" width="450">
  </a>
</p>

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Inputs](#inputs)
- [Usage](#usage)
- [Example](#example)

## Introduction

This is a composite action is built for perfoming docker build operation on the desired file with custom parameter such as tags, build agruments and location of Dockerfile.

## Features

Some functionalities that this actions offers are:

* Give custom tags to the image that you are building with the help of this action.
* Configurable file location for Dockerfile.
* Custom build arguments for passing build time variables.


## Inputs

| Inputs  | Required | Default |
|---------|----------|---------|
|FILE_LOCATION|false|.|
|IMAGE_TAG|true| |
|IMAGE_VERSION|false| |
|BUILD_ARGUMENT|false| |
|ARGUMENT_VALUE|false| |


## Usage

```yaml
- name: Docker build
        uses: virtuecloud/Composite_actions/Docker_build@main
        with:
             FILE_LOCATION: ${{github.event.inputs.FILE_LOCATION}} # Or the value which you want
             IMAGE_TAG: ${{github.event.inputs.IMAGE_TAG}} # Or the value which you want
             IMAGE_VERSION: ${{github.event.inputs.IMAGE_VERSION}} # Or the value which you want
             BUILD_ARGUMENT: ${{github.event.inputs.BUILD_ARGUMENT}} # Or the value which you want
             ARGUMENT_VALUE: ${{github.event.inputs.ARGUMENT_VALUE}} # Or the value which you want
             
```



## Example Workflow Usage

```yaml
name: Docker workflow

on:
  workflow_call:
    inputs:
      FILE_LOCATION:
        type: string
        required: false
      IMAGE_TAG:
        type: string
        required: true
      IMAGE_VERSION:
        type: string
        required: false
      BUILD_ARGUMENT:
        type: string
        required: false
      ARGUMENT_VALUE:
        type: string
        required: false
jobs:
  build-test:
    runs-on: ubuntu-20.04
    steps: 
      - name: Checkout
        uses: actions/checkout@v3
      - name: Docker build
        uses: virtuecloud/Composite_actions/Docker_build@main
        with:
             FILE_LOCATION: ${{github.event.inputs.FILE_LOCATION}} # Or the value which you want
             IMAGE_TAG: ${{github.event.inputs.IMAGE_TAG}} # Or the value which you want
             IMAGE_VERSION: ${{github.event.inputs.IMAGE_VERSION}} # Or the value which you want
             BUILD_ARGUMENT: ${{github.event.inputs.BUILD_ARGUMENT}} # Or the value which you want
             ARGUMENT_VALUE: ${{github.event.inputs.ARGUMENT_VALUE}} # Or the value which you want

```