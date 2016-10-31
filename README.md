# jenkins-ubuntu

Jenkins container based on the official jenkins image.  Build on Ubuntu.

(see official jenkins docker project https://github.com/jenkinsci/docker)

# LICENSE
MIT

# Preinstall plugins

## Generate plugins.txt from existing jenkins instance

```bash
curl -sSL "http://user:password@127.0.0.1:8080/pluginManager/api/xml?depth=1&xpath=/*/*/shortName|/*/*/version&wrapper=plugins" | perl -pe 's/.*?<shortName>([\w-]+).*?<version>([^<]+)()(<\/\w+>)+/\1 \2\n/g'|sed 's/ /:/'
```

also use:

```
RUN echo 2.0 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state
```

(see oficial link above for details)
