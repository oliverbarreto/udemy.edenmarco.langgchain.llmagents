---
title: "Goodbye CVEs, Hello `langchain_experimental`"
source: "https://blog.langchain.dev/goodbye-cves-hello-langchain_experimental/"
author:
  - "[[LangChain]]"
published: 2023-07-31
created: 2024-12-15
description: "One of the things that LangChain seeks to enable is connecting language models to external sources of data and computation. This allows language models to act as the reasoning engine and outsource knowledge and execution to other systems. Some examples of this include: * Retrieval augmented generation: Hooking a language model"
tags:
  - "clippings"
---
![Goodbye CVEs, Hello `langchain_experimental`](https://images.unsplash.com/photo-1614935151651-0bea6508db6b?crop=entropy&cs=tinysrgb&fit=max&fm=webp&ixid=M3wxMTc3M3wwfDF8c2VhcmNofDF8fGV4cGVyaW1lbnR8ZW58MHx8fHwxNjkwNjUwOTA3fDA&ixlib=rb-4.0.3&q=80&w=760)

One of the things that LangChain seeks to enable is connecting language models to external sources of data and computation. This allows language models to act as the reasoning engine and outsource knowledge and execution to other systems. Some examples of this include:

- Retrieval augmented generation: Hooking a language model up to a retrieval system and using that influence the generation. This allows language models to answer questions about information other than what they were trained on.
- Interacting with APIs: Having a language model generate the route and parameters to call for a specific API request. This allows humans to interact with an API through natural language.
- Code generation: Having a language model write and then execute code. This can enable people to generate code just by asking.

While this is powerful, it can also be dangerous. A lot has been discussed around AI safety, and there are many different types and considerations for AI safety. The type that we are most concerned with is what happens when you hook up language models to other systems. While doing this can enable lots of amazing experience (like the ones listed above) it also opens up a whole new risk vector.

This risk vector emerges when the language model generates output that is unsafe to pass downstream, whether that be an API request that deletes some data or some malicious code that deletes all files. This can occur naturally or maliciously. It can occur naturally when the language model simply messes up - as its prone to do. It can also occur maliciously, through techniques like prompt injection.

LangChain started off as highly experimental and included a lot of these use cases, as those uses were the ones pushing boundary of what was possible. Some of these use cases have security concerns, some don’t. As LangChain matures, we want to better separate those uses to allow for that distinction.

We’ve taken a first stab at that by releasing `langchain_experimental`, a separate Python package. We’ve moved all components that raised CVEs into that package. We’ve also moved everything previously in the `langchain.experimental` module there as well. You can find instructions on how to migrate [here](https://github.com/langchain-ai/langchain/blob/master/MIGRATE.md?ref=blog.langchain.dev).

Going forward, we have the dual goals of making core `langchain` more robust and production ready, while also pushing forward rapidly with `langchain_experimental`. We’ve been slow to accept some more experimental features, but this separation will now hopefully speed that up.

We will also likely move more things over to `langchain_experimental` over time. When we do this, we will always give at least a week’s notice before making any breaking changes, and update the [migration guide](https://github.com/langchain-ai/langchain/blob/master/MIGRATE.md?ref=blog.langchain.dev).

We’d like to thank the entire community for understanding, as well as their patience as we iron out any kinks. In particular we’d like to thank some community members for their help and encouragement on this: Rich Harang (and the entire Nvidia team), Justin Flick, Or Raz, and Boaz Wasserman.

### Tags

### Join our newsletter

Updates from the LangChain team and community

Enter your email

Processing your application...

Success! Please check your inbox and click the link to confirm your subscription.

Sorry, something went wrong. Please try again.