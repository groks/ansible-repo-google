repo-google
========

An [ansible role](https://galaxy.ansible.com/groks/repo-google/) to install
the following yum repositories for Google software:

- [google-chrome](https://www.google.com/intl/en/chrome/browser/desktop/index.html)
- [google-talkplugin](https://www.google.com/tools/dlpage/hangoutplugin)
- [google-musicmanager](https://play.google.com/music/listen#/manager)
- [google-earth](http://www.google.com/earth/)
- [google-cloud-sdk](https://cloud.google.com/sdk/downloads#yum)

After enabling the role you **must** explicitly install the packages you want:

    ---
    - hosts: localhost

      roles:
        - groks.repo-google

      tasks:
        - name: install google software
          dnf: name={{ item }} state=present
          with_items:
            - google-chrome-stable
            - google-chrome-beta
            - google-chrome-unstable
            - google-talkplugin
            - google-musicmanager
            - google-cloud-sdk
            - google-cloud-sdk-app-engine-python
            - google-cloud-sdk-datastore-emulator
            - google-cloud-sdk-pubsub-emulator
            - kubectl


Get a list of the available packages by running the following command:

    dnf --disablerepo='*' --enablerepo='*google*' list available

Requirements
------------

An installation of Fedora, RedHat, CentOS etc.

Role Variables
--------------

The repos in the list variable `repo_google_all` will be installed and enabled,
which by default is all of them:

    repo_google_all:
      - chrome
      - talkplugin
      - musicmanager
      - earth
      - cloud-sdk

You can set this list to a subset of those available. For example:

    ---
    - hosts: localhost

      vars:
        repo_google_all:
          - chrome
          - talkplugin

      roles:
        - groks.repo-google

Dependencies
------------

None.

License
-------

BSD
