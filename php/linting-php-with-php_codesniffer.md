# Linting PHP with PHP\_CodeSniffer

Please also see the installation in [Air-light Debuggers](https://github.com/digitoimistodude/air-light#debuggers) or on [Internal Development Docs](https://app.gitbook.com/o/PedExJWZmbCiZe4gDwKC/s/VVikkYgIZ9miBzwYDCYh/). Your editors should lint automatically after installing these tools.

### Disabling rules

If for some reason you need to use something that has been disallowed in phpcs.xml you should have good arguments in favor of it. You should comment the change accordingly:

\`\`\`php

### PHP Code Beautifier and Fixer (phpcbf)

With phpcbf it's quick to fix the most common errors that are not right accoring to your project phpcs.xml.

```bash
phpcbf --standard=phpcs.xml page.php
```

### General linting and coding rules

You should always comment your code as thorough as possible. For indentation we use to char space. Always use the latest .editorconfig:

{% embed url="https://github.com/digitoimistodude/devpackages/blob/master/.editorconfig" %}
