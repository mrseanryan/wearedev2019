# Building AI assistants that scale using machine learning and OSS tools

Justina Petraityte - company: RASA

- RASA = a chatbot OSS framework, with ML capability

## setup

1. Installing python3 + pip + rasa

`install.sh`

2. [optional] Installing ngrok
https://ngrok.com/download

"One command for an instant, secure URL to your localhost server through any NAT or firewall."

## refs

https://github.com/rasaHQ/workshop-rasax

https://rasa.com/docs

## notes

- edited nlu.md (training data for chat)
- view (not edit) yml file - config.yml = configuring the model
- train the model:

```shell
cd workshop-rasax
rasa train nlu
```

- run:

```shell
rasa shell nlu
```

- type a message -> get back JSON - confidence, entities, intents (ranked)

`stories.md` = real data from user sessions

`domain.yml` = actions, entities, templates (how assistant responds for an action)

- lookup tables = lists of entity values (like locations, names ...)

### rasa

- uses a RNN (Recurrent NN) to take previous conversations into account (conversation history)

- user-text -> [intent, entities] -> RNN -> next-best-action -> API or text response

- python(3) based
- uses scipy (tensorflow)

- rasa core
- custom actions (python) - rasa core sdk

- `rasa init` to create a new project, with files already created.

- `rasa shell` - to interactively test your chat

- visualize the training data, as a graph

- `rasa test` - cross validation test
- other testing - via test users ??

- need to avoid biased data (e.g. generated from a small number of users)

- `rasa x` = a UI based tool

## tips

- allow real users to use and give feedback
- give something simple, get feedback early
- when needed, use business logic (rules, state machines - old-school - use cases where something DOES need to be done)
- customize OSS (rather than code self?)
- keep stories short (10 lines!) - else need lot of RAM
- use different bots for different domains (e.g. weather, restaurant booking, hotel booking)
- a bot to switch between bots? - difficult to train? - a 'receptionist'
- there are starter packs (a bot about rasa, a bot about healthcare)
- typo handling - can build custom components (python has some) - stemming, Levenshtein distance... - typo correction model?

### how much data needed?
- at least 15-20 examples for each intent
- basic bot: 2-3 actions: at least 10-20 conversations to learn from.
- 50-100 conversations better; 50-100 NLU (Natural Language Understanding) examples
- BUT start small (small number of examples)
