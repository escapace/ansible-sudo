# ansible-sudo

Installs `sudo` on CentOS Stream 10 and leaves the packaged `/etc/sudoers` in place. By default, members of `wheel` can run sudo commands without a password.

## Variables

- `sudo_wheel_nopasswd` defaults to `true` and accepts a boolean. Set it to `false` to remove this role's passwordless rule from `/etc/sudoers.d/`; the packaged password-requiring `%wheel` rule then applies unless other sudoers files override it.

The role does not manage wheel membership or other sudoers files. Because sudoers uses the last matching rule, another later drop-in can override this role's rule. `sudo -v` can still prompt for a password because the packaged password-requiring wheel rule remains.
