# Sidekick

![Sidekick](docs/images/sidekick.png)

## Table of contents

- [Sidekick](#sidekick)
  - [Table of contents](#table-of-contents)
  - [Description](#description)
  - [Why Sidekick?](#why-sidekick)
  - [Features](#features)
  - [Guided tour](#guided-tour)
  - [Quick start](#quick-start)
  - [About](#about)
  - [License](#license)
  - [Prerequisites](#prerequisites)
  - [More detailed installation options](#more-detailed-installation-options)
  - [Usage](#usage)
  - [Roadmap](#roadmap)

## Description

Sidekick is an AI powered tool for creativity, thinking, exploring ideas, problem-solving, knowledge-building, and getting things done.

It provides a chat interface to OpenAI's GPT models along with pre-canned AI personas and a prompt fragment library to help you get more out of the AI and a working environment where you can create notes by selecting the most interesting and useful parts of the chat to edit and organise into a more complete text aligned with what you want.

## Why Sidekick?

Everyone has access to Generative AI in the form of ChatGPT and other tools. However most of these tools are designed for general use and are built on top of APIs that are more powerful under the hood. Many of the out-of-the-box tools also use the prompts users enter to further train their models. This is generally not the case for the APIs.

Sidekick is intended as a tool for people who want to use Generative AI to help them think, explore ideas, solve problems, build knowledge, and get things done. It is designed to be easy to use and to help you get the most out of the AI.

It's also using the APIs directly, so once you get your API key you can deploy Sidekick wherever you want and use it without having to worry about your prompts being used to train the AI. As all the code is provided you can also extend it or modify it to suit your needs.

GenAI has much more potential than chat. OpenAI have been making it easier to build on the models by adding features to the API. For example, You can write a program to call GPT-4 and tell it about other APIs you have access to and what they do so that as part of GPT-4's response to your prompt, it can ask you to make calls to those other APIs to get more information. This means you can integrate the 'AI in the cloud' to other information sources you have, and use its intelligence to build automations and enable it to answer questions based on realtime data or data only you have access to.

Sidekick v0 is the beginning of a project to provide a platform for extending and integrating AIs with information sources and other APIs to build a new kind of AI-powered tool for creativity, thinking, exploring ideas, problem-solving, knowledge-building, and getting things done.

You can either just deploy this and let it run, or you can use it as a starting point to build your own AI-powered tools.

## Features

- Chat with an AI
- Change the persona of the AI
- Compose your prompt from a library of fragments
- Create and edit notes
- Augment notes with the best parts from your chats
- Export notes
- Import notes
- Chat with your notes, e.g.
  - Ask questions about your notes
  - Ask for a summary of your notes
  - Ask for a summary of your notes on a specific topic


## Guided tour
![Logon page](docs/images/Sidekick_Login.png)

## Quick start

> [!IMPORTANT]
> You will need an OpenAI API key to use the AI features. You can get an OpenAI API key [here](https://beta.openai.com/).

Clone the repository, e.g.:

- With GitHub CLI: `gh repo clone embernet/sidekick`
- With Git: `git clone git@github.com:embernet/sidekick.git`

Create a `.env` file in the `sidekick/server` directory with the following contents:

  ```bash
  OPENAI_API_KEY=<your OpenAI API key>
  ```

Build the docker containers and start the application.

  ```bash
  cd sidekick
  make build && docker-compose up -d
  ```

Using -d will run the docker containers as deamons in the background. In this case, you can close the terminal window and the application keeps running. Currently this application is in pre-release, and both server processes provide logs to their console. If you want to see this, run them in the foreground by omitting the `-d` flag; in this case, you will need to keep the terminal window open while you are using it.

You should now have two docker containers running: `sidekick-server` and `sidekick-web-ui`. You can check this with `docker ps`.

> [!NOTE]
> When the application is run from docker containers as above, the server is running on [http://localhost:5004](http://localhost:5004) and the web UI is running on [http://localhost:8081](http://localhost:8081).
> If you decide to run the application locally, the server is running on [http://localhost:5003](http://localhost:5003) and the web UI is running on [http://localhost:8080](http://localhost:8080).

## About

This project is in active development, however each release is intended to be ready to use and feature complete as far as it has so far been developed.

[Contribution guidelines for this project](docs/CONTRIBUTING.md)

## License

[MIT License](LICENSE.txt)

## Prerequisites

- You will need your own OpenAI API key to use this application. You can get one [here](https://beta.openai.com/).
- pipenv, npm, python3, more details below

## More detailed installation options

1. [Install in a docker container](docs/docker-installation.md)
2. [Install locally](docs/local-installation.md)

To see how to change the way the application is installed and run and where it stores its settings and data, see the [configuration guide](docs/configuration.md).

## Usage

1. Getting started
   1. Start the application by running `docker-compose up` if you are running from a docker container or `npm start` if you installed locally
   2. The application should automatically open in your browser. Or you can browse to [http://localhost:8081] if you are running from a docker container or [http://localhost:8080] if you installed locally
2. From the home page
   1. Click the `Explore Chats` button to show or hide the Chat Explorer view
   2. Click the `Chat` button to show or hide the Chat Window
   3. Click the `Notes` button to show or hide the Notes Explorer view
   4. Click the `Personas` button to change the persona of the AI
   5. Click the `Prompt Composer` button to show or hide the prompt composer
3. When in the Chat Window
   1. Enter a prompt
   2. Click the `Chat` button or hit return to chat with the AI
   3. Chats are saved automatically
   4. Click in the name field at the top of the chat if you want to rename it. Escape clears the name so you can enter a new one.
4. Right click on a chat to
   1. Copy it to the clipboard
   2. Append to chat input, e.g. to refer to all or part of a previous response
   3. Use as chat input, e.g. to edit and continue the conversation
   4. Append to note, e.g. to save the most interesting and useful parts of the chat
   5. Append all to note, to save the whole chat into a note along with other chats or your own notes or to edit it
   6. Delete it from the chat history so it doesn't impact the AI's future responses
   7. Delete all messages to clear the chat and start again
5. Click the `Notes` button to show or hide the Notes Explorer view
6. From the Notes Explorer view
   1. Filter notes by name
   2. Bulk delete filtered notes that are no longer required
   3. Click on a note to edit it (there is a delete button in the note editor if you want to delete it)
7. When in a Note
    1. Click the `Export` button to download a note as a local text file
    2. Click the `Import` button to import a local text file into the current note
    3. Enter a prompt at the bottom of the note and click the `Chat` button or hit return to chat with the AI about the note
8. Click the `Model Settings` button to open the Model Settings, where you can:
    1. Change the model
    2. Change the temperature and other model settings to alter (creativity / consistency) of the response

## Roadmap

This project is in active development. You can see the roadmap [here](docs/ROADMAP.md).
