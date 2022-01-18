---
description: >-
  This documentation will guide a dude employee trough of starting a new
  project.
---

# Starting a new project

{% hint style="info" %}
**Please note:** You can also find the setup instructions of our WordPress stack at its own GitHub repository section [dudestack/instructions](https://github.com/digitoimistodude/dudestack-instructions).
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

First, log in to staging server:

```bash
ssh account@gunship.dude.fi
```

Second, log in to MariaDB server:

```bash
mysql -u root -p
```

Let's create credentials for your project:

```sql
CREATE USER 'projectname'@'%' IDENTIFIED BY 'YOUR_MEGA_LONG_AND_ULTRA_DIFFICULT_PASSWORD_GENERATED_IN_1PASSWORD';
```

Then we are going to grant all the necessary permissions for that user:

```sql
GRANT ALL PRIVILEGES ON projectname.* TO 'projectname'@'%';
```

Let's apply the changes by flushing privileges:

```sql
FLUSH PRIVILEGES;
```

Next, upload the database to Gunship with [**Sequel Pro Nightly**](https://sequelpro.com/test-builds) with following steps.

1. Open Sequel Pro
2. Connect to your local database
3. Select _Choose Database.._, select your database from the list
4. Go to app menu: _File > Export.._ Ensure SQL-tab and all the tables are selected, click _Export_.
5. Open new tab and connect to gunship.dude.fi
6. Select _Choose Database... >_ _Add Database..._, name your project the same name you have in local
7. Ensure you are in your newly created database and then go to app menu: _File > Import_... and select your local database.

Your shared project database is now ready.

Next you'll need to change your project database credentials to be used by our staging server gunship.dude.fi.

So open the `.env` file in your project root. It may look like this:

```javascript
DB_NAME=textdomain
DB_USER=root
DB_PASSWORD=password
DB_HOST=127.0.0.1

WP_ENV=development
WP_HOME=https://textdomain.test
WP_SITEURL=https://textdomain.test/wp
AUTH_KEY='_M`_z/S6v$5+db{8Z`p[#Vpzv S^sh<aT*_)^AL/ac>de%@34<MCJ224LgG3ot38'
SECURE_AUTH_KEY=':LO#@{9@>X%,yMW>A;r9X)A.}6Yb}o! ZkVw:q.{%9(?iB<Iwfe-{F%#?z$]NJ7|'
LOGGED_IN_KEY='UowQFrBg}fe.G=D3?HJ[$kW@JvV[5o[lDf18w~%j.)dB@H`!%AUOKcl)y73~_Mbk'
NONCE_KEY='S3)^ST]Ny>^:v57:+nKBpVhNp!D/jEi1,<CMGn{5b02wsvskI2MYkU?ArBxA6F>Z'
AUTH_SALT='sq?ZE[rFK-23b-$KJm;U6,-[udj}J/M1oKnTuE]5kMumt.X2gSj$M`W6,6TC4=`)'
SECURE_AUTH_SALT='CdyXIipSVJ5%EoDK7NkfD6#xyr0~jQ8MU=:>blHWV|x{n1w_bG<E?Z1x*nm<4-zl'
LOGGED_IN_SALT='$w|%HHx>GV%Uj:BkCpOB%cZRq#F_T5=s<+,vzrj5$]l -N,j2ILDK/_19mIo*AH5'
NONCE_SALT='sB}RS:js-vb19.@yDi1$fJB^V9~z:x+pY*7d%&vU?xi7r)+U>Tu.>W9JsZ9o 0DH'

SENDGRID_API_KEY=apikey
IMAGIFY_API_KEY=apikeya
ACF_PRO_KEY=apikey
MAILGUN_API_KEY=apikey
DUDE_API_KEY=apikey
MAILGUN_USE_API=yes
```

Change it to this:



#### 4. Save credentials and file sync for others to collaboration

Open your `.env` file
