---
description: >-
  This documentation will guide a dude employee trough of starting a new
  project.
---

# Starting a new project

{% hint style="info" %}
Please note: You can also find the setup instructions of our WordPress stack at its own GitHub repository section [dudestack/instructions](https://github.com/digitoimistodude/dudestack-instructions).
{% endhint %}

### Introduction

Even though our ways are mostly automated, there are some tasks that are not worth of automating in sake of effectiveness. The developers that jump in later are not able to use the project starting commands, therefore some things need attention separately as per [How to continue developing a project that has been already started](https://handbook.dude.fi/wordpress-kehitys/projektin-aloitus#:\~:text=Projektin%20aloitus-,My%C3%B6hemmin%20projektiin%20mukaan%20tulevat,-Hand%20off%20suunnittelijalta).

## Getting started

#### 1. Creating a new project

Kickstart the new project by running the following command:

```bash
createproject
```

This script will ask all the necessary details about the project like project name. After this automation will create the basics for project as per [digitoimistodude/dudestack](https://github.com/digitoimistodude/dudestack) and virtual host and host entry for the local development environment as per [digitoimistodude/macos-lemp-setup](https://github.com/digitoimistodude/macos-lemp-setup).

{% hint style="info" %}
The createproject command consists of bunch of different tasks. You can view the source code of these tasks on [GitHub](https://github.com/digitoimistodude/dudestack/tree/master/bin).
{% endhint %}

#### 2. Creating a WordPress theme for the project

Next you will need to create a theme for the project by running the following command:

```bash
newtheme
```

This command will create a WordPress theme based on [Air-light](https://app.gitbook.com/o/PedExJWZmbCiZe4gDwKC/s/3wjKHwxi1Rn1DobDRUuf/) for our project.

{% hint style="info" %}
The createproject command consists of bunch of different tasks. You can view the source code of these tasks on [GitHub](https://github.com/digitoimistodude/air-light/tree/master/bin).
{% endhint %}

#### 3. Creating a shared database for the project

Next we will need a shared database for our project to our staging server (gunship). The start scripts in steps 1 and 2 have already established a local development database but as we need to share the work we do with the developer fella next to us, we need to get it shared. Also this way everything keeps in sync with the customer and all developers without us having continuously figure out on how to migrate without conflicts.
