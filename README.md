
# BotLis

BotLis is a simple, customizable Python bot framework that allows you to create your own commands and event hooks. It is lightweight, modular, and easy to extend.

---

## Project Structure


botlis/
├─ main.py           # Main entry point to run the bot
├─ sources/
│   └─ btsource.py   # Bot module containing the CustomBot class



---

## Installation

1. Clone or download this repository.
2. Make sure you have Python 3.7+ installed.
3. No external dependencies are required.

---

## Usage

### 1. Import the bot module

```python
from sources.btsource import onstart
````

### 2. Create the bot

```python
bot = onstart("YOUR_CUSTOM_BOT_TOKEN")
```

### 3. Register custom commands

```python
# Example commands
def hello(*args):
    print("Hello! Args:", args)

def stop(*args):
    bot.onstopresponding()

def ping(*args):
    tag = args[0] if args else "@unknown"
    bot.onping(tag)

# Register commands
bot.register_command("hello", hello)
bot.register_command("stop", stop)
bot.register_command("ping", ping)
```

### 4. Run the bot

```python
bot.run()
```

---

## Event Hooks

The bot provides the following event hooks that you can override if needed:

* `onstart()` — triggered when the bot starts
* `oncommand(cmd, *args)` — triggered on any command input
* `onping(at_tag)` — triggered when a ping command is executed
* `onstopresponding()` — triggered when the bot stops
* `onerror(msg)` — triggered on errors during execution

---

## Example

```python
from sources.btsource import onstart

bot = onstart("MY_CUSTOM_BOT_TOKEN")

def hello(*args):
    print("Hello!", args)

def stop(*args):
    bot.onstopresponding()

bot.register_command("hello", hello)
bot.register_command("stop", stop)

bot.run()
```

---

## Notes

* All commands must be registered using `register_command`.
* The bot reads input from the console by default.
* You can extend the bot by creating more commands or overriding event hooks.

---

## License

This project is open-source and free to use.

