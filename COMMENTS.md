# How to run
```
vagrant up (or vagrant up --provision)
```

You can also run
```./provision.sh``` which ensures it starts with a clean, fresh state

# How it works
In a very high level, it does the following:
- unzip application.zip to /opt/application
- registers theapplication with systemd (see templates/app.service.j2), and listens on port 8000
- nginx acts as a proxy server, it does a few things:
    - redirects http to https (status code 301)
    - uses self-signed ssl cert
    - expose port 8000 to port 80

# Notes:
- vars/application.yml, application specific variables
- template, folder to hold app level template files
- files, app files such as ssl cert and key
- roles, playbook required roles (with the intention to have greater modularity and code-reuse, although it is probably overkill for this exercise)
