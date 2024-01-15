# Why is this necessary?

CELAUT intend to solve is precisely the separation between the “*how to solve a problem*” and the “*where and who solve it*”.

Take, for example, a trading bot.

<aside>
💡 Trading bots are automated software programs that execute buy and sell orders in financial markets based on predefined algorithms. They are important as they can operate 24/7, react quickly to market changes, and remove emotional biases, enhancing efficiency and consistency in trading strategies.

</aside>
<br>
In this context, if you want to use a trading bot right now, You will go to the web and can:

1. Look for a web service that will manage your asset portfolio, which has:
    1. Advantages:
        1. You don’t need to run the infrastructure yourself.
        2. You don’t need to configure anything.
    2. Disadvantages:
        1. You can’t attribute reputation to it because the developer of the web
        service is unable to prove that the system hasn’t changed (for example,
        when a bot has gained a large number of users, they might reduce
        its performance to encourage you to use a newer one).
        2. The developers of the web service can’t assure you that they aren’t
        misusing the data from your requests (in this case, the
        movements of your portfolio).
2. Search for a source code (on GitHub, etc.) that you can run on your PC (or in the cloud) on your own.
    1. Advantages:
        1. It’s deterministic, in the sense that (if it can’t connect to the
        internet) you’ll be sure that its behavior and/or performance won’t change in the future, because the developer can't modify the source that you previously downloaded.
        2. The developer of the service has no control over the data of your requests.
    2. Disadvantages:
        1. You need to possess equipment (infrastructure) capable of running the code.
        2. You have to deal with system configuration issues (which are often
        significant enough for an average user to opt for a web service).

In contra part of this two options, CELAUT allows to take the advangates of the two previous solutions without their disadvantages. There’s why:

- You don’t need to run the infrastructure yourself or search for a cloud provider to do that, as the node takes care of this.
- You don’t need to configure anything, as the specification service covers how the container is built, his architecture, his network requirements and his interface, the user don’t need to know anything about that.
- The developers of a service cannot control, modify or extract data of the service as they don’t control the nodes that distribute and runs it. Although they could be incentivized to develop it.