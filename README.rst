Err - the pluggable jabber bot
==============================

Err is a plugin based XMPP chatbot designed to be easily deployable, extensible and maintainable.
It is written in python and it is based on jabberbot_ and yapsy_ with some minor modifications for the first one.

Err has a google_ plus_ page_, feel free to mention it with +err if you need support, have any questions, share some of your creations etc ...

Brief History
-------------

At Mondial Telecom (http://www.mondialtelecom.eu), we needed a chat bot over XMPP so it can reach the non techie audience of the company.
We started to write so much features that we decided to make a more modular bot framework.

Features
--------

- Tested with hipchat_ and openfire_ but should be compatible with any XMPP/Jabber servers.
- Can be setup so a restricted list of persons have the administration rights
- Dynamic plugin architecture : the bot admin can install/uninstall/enable/disable plugins dynamically just by chatting with the bot.
- Supports MUCs (chatrooms)
- Can proxy and route one 2 one messages to MUC so it can enable simpler XMPP notifiers to be MUC compatible (for example the jira XMPP notifier).
- Really easily extensible (see example below)
- Provides an an automatic persistance store per plugin
- an !help command that generate dynamically the documentation from the python docstrings of the commands

.. _hipchat: http://www.hipchat.org/
.. _openfire: http://www.igniterealtime.org/projects/openfire/
.. _jabberbot: http://thp.io/2007/python-jabberbot/
.. _yapsy: http://yapsy.sourceforge.net/
.. _google: https://plus.google.com/101905029512356212669/
.. _plus: https://plus.google.com/101905029512356212669/
.. _page: https://plus.google.com/101905029512356212669/

Prerequisites
-------------
Create a user for the bot on your private XMPP server or a public server like jabber.org.
Optionally you can create a MUC (also called conference room or chatroom) in which you can interact with the bot. 


Installation from the sources
-----------------------------

**Dependencies**

Python 2.7+ but probably not 3.0
And those python modules. The copy-paste for the lazy pip users but if you can have them from your standard distro it is better
::
    pip install -r requirements.txt

Create a user for the bot in your XMPP server admin.

From the installation directory copy
::
    cp errbot/config-template.py config.py

Read the inline documentation of the file and edit the values so the bot can connect to your XMPP server

**Starting the daemon**

For a one shot try, I would recommend to use
::
    ./scripts/err.py

Then you can use the -d (or --daemon) parameter to run it in a detached mode.
::
    ./script/err.py -d

so you can inspect the logs for an immediate feedback

Note that config.py needs to be at the root of the working directory of the bot by default.

You can override this behaviour with -c specifying the directory where your config.py is, for example
::
    ./script/err.py -c /etc/err

More details on the bot admin features can be found on the wiki : https://github.com/gbin/err/wiki/admin

Installation from pypi
----------------------

Pip will take care of installing err and the basic dependencies for you
::
    pip install err

Go to or create a working directory for it then copy there and adapt the configuration template
::
    cp /usr/lib64/python2.7/site-packages/errbot/config-template.py config.py

Then you can start and try your bot
::
    err.py


Interact with the Bot
---------------------

- Invite the bot directly from your chat client.
- Send "!help" to it without the quotes
- it should answer by the list of available commands and a short explanation
- if you want to know more about a command you can do "!help command"

More documentation is available on the wiki : https://github.com/gbin/err/wiki

Install/uninstall a public known plugin
---------------------------------------

To get a list of public repo you can do
::
    !repos

Then pick one that you fancy for example
::
    !install err-pollbot

You should have instantly a new poll service you can use to vote for where to lunch with you collegues :)

You can imply uninstall a plugin by its name:
!uninstall err-pollbot

Note: Please pay attention when you install a plugin, it may require more python external dependencies.

Tutorial to write a simple plugin
---------------------------------

Try it ! It is super simple !

You can find a tutorial here : https://github.com/gbin/err/wiki/plugin-dev

