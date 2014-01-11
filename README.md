repo-google
========

An [ansible role](https://galaxy.ansibleworks.com/list#/roles/200) to install
the following yum repositories for Google software:

- [google-chrome](https://www.google.com/intl/en/chrome/browser/)
- [google-talkplugin](https://www.google.com/tools/dlpage/hangoutplugin)
- [google-musicmanager](https://play.google.com/music/listen#/manager)
- [google-earth](http://www.google.com/earth/)

After enabling the role you must explicitly install the packages you want:

    ---
    - hosts: localhost

      roles:
        - groks.repo-google

      tasks:
        - name: install google software
          yum: name={{ item }} state=present
          with_items:
            - google-chrome
            - google-talkplugin
            - google-musicmanager

Get a list of the available packages by running the following command:

    yum --disablerepo='*' --enablerepo='*google*' list available

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
