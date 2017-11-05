# jenkins-ubuntu

Jenkins container based on the official jenkins image.  Built on Ubuntu.

(see official jenkins docker project https://github.com/jenkinsci/docker)

latest will now always track the latest LTS version from jenkins
(triggered from their jenkins/jenkins).

I've layered on a few useful tools like:
* git v2
* wget / curl
* vim
See the Dockerfile for details.

As such, this image is somewhat larger than the official image...

Be sure to map a persistent volume to /var/jenkins_home.

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

(see official link above for details)
