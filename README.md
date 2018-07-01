# uniborg

Pluggable [``asyncio``](https://docs.python.org/3/library/asyncio.html)
[Telegram](https://telegram.org) userbot based on
[Telethon](https://github.com/LonamiWebs/Telethon).

## installing

Simply clone the repository and run the main file:
```sh
git clone https://github.com/uniborg/uniborg.git
cd uniborg
python stdborg.py
```

## design

The modular design of the project enhances your Telegram experience
through [plugins](https://github.com/uniborg/uniborg/tree/master/stdplugins)
which you can enable or disable on demand.

Each plugin gets the `borg`, `logger` and `storage` magical
[variables](https://github.com/uniborg/uniborg/blob/4805f2f6de7d734c341bb978318f44323ad525f1/uniborg/uniborg.py#L66-L68)
to ease their use. Thus creating a plugin as easy as adding
a new file under the plugin directory to do the job:

```python
# stdplugins/myplugin.py
from telethon import events

@borg.on(events.NewMessage(pattern='hi'))
async def handler(event):
    await event.reply('hey')
```

## internals

The core features offered by the custom `TelegramClient` live under the
[`uniborg/`](https://github.com/uniborg/uniborg/tree/master/uniborg)
directory, with some utilities, enhancements and the core plugin, which
can be unloaded in itself (something fun to do, but you will probably
want to restart your borg after).

## learning

Check out the already-mentioned
[plugins](https://github.com/uniborg/uniborg/tree/master/stdplugins)
directory to learn how to write your own, and consider reading
[Telethon's documentation](http://telethon.readthedocs.io/).
