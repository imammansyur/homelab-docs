# User and Group Management

## User Management

### Creating User

To create a user, you can use `useradd` on common linux or `adduser` for Alpine Linux. `useradd [username]` works, but in most cases, you'd want to also make the home folder. In that case, you need to add `-m` tag.

```
useradd -m [username]
```

### Setting Up User Password

You can setup user password with this command:

```
passwd [username]
```

### User Modification

To modify a user, you can use `usermod`. There are multiple cases like adding user to group or changing shell.

```
# Add user to group
usermod -aG group [username]

# Change user's shell
usermod -s /bin/zsh [username]
```
