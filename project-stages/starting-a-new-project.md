---
description: This documentation will guide you trough of starting a new project.
---

# Starting a new project

{% hint style="info" %}
Please note: You can also find the setup instructions of our WordPress stack at its own GitHub repository section [dudestack/instructions](https://github.com/digitoimistodude/dudestack-instructions).
{% endhint %}

### Introduction

Even though our ways are mostly automated, there are some tasks that are not worth of automating in sake of effectiveness. The developers that jump in later are not able to use the project starting commands, therefore some things need attention separately as per [How to continue developing a project that has been already started](https://handbook.dude.fi/wordpress-kehitys/projektin-aloitus#:\~:text=Projektin%20aloitus-,My%C3%B6hemmin%20projektiin%20mukaan%20tulevat,-Hand%20off%20suunnittelijalta).

## Getting started

1\. Kickstart the new project by running the following command:

```bash
createproject
```

This script will ask all the necessary details about the project like project name. After this automation will create the basics for project as per [digitoimistodude/dudestack](https://github.com/digitoimistodude/dudestack) and virtual host and host entry for the local development environment as per [digitoimistodude/macos-lemp-setup](https://github.com/digitoimistodude/macos-lemp-setup).

2\. Next you will need to create a theme for the project by running the following command:

