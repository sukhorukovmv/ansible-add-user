## What is ansible-user? 

It is an role to:

- Create user groups
- Create a single user, add it to any groups you created and configure its shell
- Set your public SSH key as an authorized key so you can login without a password
- Enable passwordless sudo

## Why would you want to use this role?

When you spin up a new server, you'll often want to set up a non-root user that
you can login as and run your applications under. That's because running your
applications as root is a questionable idea from a security point of view.

This role sets you up to do that, but it also includes a few other user related
tasks, such as what's listed in the above bullets. Having all of these things
together in 1 role means less work for you to do!

## Supported platforms

- Ubuntu 16.04 LTS (Xenial)
- Ubuntu 18.04 LTS (Bionic)
- Debian 8 (Jessie)
- Debian 9 (Stretch)

## Role variables

```
# Optionally create additional user groupss. If empty, the user you create will
# automatically be a part of their user's group, ie. deploy:deploy.
user_groups: []

# The user you want to create.
user_name: "sukhorukovmv"

# Which shell should you default to? Typically "bash" or "sh".
user_shell: "/bin/bash"

# Do you want to create an SSH keypair for this user? You probably don't for a
# regular user that you plan to login as which is why it's disabled by default.
user_generate_ssh_key: False

# When set, this will copy your local SSH public key from this path to your
# user's authorized keys on your server.
#
# If you don't want this behavior then use an empty string as the value but keep
# in mind this role does not set a default password for the user you create, so
# you will be locked out if you don't supply your public SSH key.
user_local_ssh_key_path: "~/.ssh/id_rsa.pub"

# Do you want to enable running root commands without needing a password?
user_enable_passwordless_sudo: True
```

