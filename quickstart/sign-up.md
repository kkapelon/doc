---
description: Sign up to Qovery
---

# Sign Up

To sign up using [Qovery CLI](../extending-qovery/cli.md), it's simple:

{% hint style="info" %}
First time using Qovery?[ **install the Qovery CLI**](../extending-qovery/cli.md).
{% endhint %}

Then run the following command:

```text
$ qovery auth
```

You'll get a window open on your browser to link with your account. In this example we chose GitHub

![](../.gitbook/assets/qovery_auth.png)

Qovery needs to access to your account \([click here](https://github.com/apps/qovery/installations/new)\) to be able to clone your repository for future application build. 

![](../.gitbook/assets/github_connect.png)

Then we need to validate it on our side:

![](../.gitbook/assets/github_auth.png)

That's it, you should have a message saying: "_Authentication successful. You can close this window_."

