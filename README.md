## Introduction

This document explains how to set up a script to switch between multiple Git users easily. The script allows you to switch between different configurations, such as Developer, Freelancer, and other dummy users. With this solution, users can easily switch Git user configurations for different purposes like personal development, work, and more.


#### Prerequisites
Before proceeding with this setup, ensure that you have the following:

- A Unix-based system (Linux/MacOS) with Git installed.
- A text editor (like nano or vim) for editing files.
- Access to the terminal for running commands.



Step-by-Step Guide
- Create the Switching Script
Open a terminal and create a new script file using a text editor (e.g., nano):
```
nano ~/git-use.sh
```

- Add the following content to the script or Update in our script "**git-use.sh**":

```
# Git User Details (User should modify these variables)
DEVOPS_NAME="devops"
DEVOPS_EMAIL="yourdevops@gmail.com"

FREELANCER_NAME="freelancer"
FREELANCER_EMAIL="yourfreelancer@gmail.com"

DUMMY1_NAME="dummyuser1"
DUMMY1_EMAIL="dummy1@example.com"

DUMMY2_NAME="dummyuser2"
DUMMY2_EMAIL="dummy2@example.com"

DUMMY3_NAME="dummyuser3"
DUMMY3_EMAIL="dummy3@example.com"

# Function to set Developer user
set_devops() {
  git config --global user.name "$DEVOPS_NAME"
  git config --global user.email "$DEVOPS_EMAIL"
  echo "Switched to Developer user: $DEVOPS_NAME"
}

# Function to set Freelancer user
set_freelancer() {
  git config --global user.name "$FREELANCER_NAME"
  git config --global user.email "$FREELANCER_EMAIL"
  echo "Switched to Freelancer user: $FREELANCER_NAME"
}

# Function to set Dummy User 1
set_dummy1() {
  git config --global user.name "$DUMMY1_NAME"
  git config --global user.email "$DUMMY1_EMAIL"
  echo "Switched to Dummy User 1: $DUMMY1_NAME"
}

# Function to set Dummy User 2
set_dummy2() {
  git config --global user.name "$DUMMY2_NAME"
  git config --global user.email "$DUMMY2_EMAIL"
  echo "Switched to Dummy User 2: $DUMMY2_NAME"
}

# Function to set Dummy User 3
set_dummy3() {
  git config --global user.name "$DUMMY3_NAME"
  git config --global user.email "$DUMMY3_EMAIL"
  echo "Switched to Dummy User 3: $DUMMY3_NAME"
}

# Switch based on the first argument
case "$1" in
  devops)
    set_devops
    ;;
  freelancer)
    set_freelancer
    ;;
  dummy1)
    set_dummy1
    ;;
  dummy2)
    set_dummy2
    ;;
  dummy3)
    set_dummy3
    ;;
  *)
    echo "Usage: git use devops | freelancer | dummy1 | dummy2 | dummy3"
    ;;
esac

```

- Save and exit the editor (CTRL+X, then press Y and Enter).




#### Make the Script Executable

Run the following command to make the script executable:

```
chmod +x ~/git-use.sh

```



#### Create the Git Alias for Easy Use

To easily use the script with Git, you need to create an alias for it.

- Open your global Git configuration file using the following command:

```
git config --global --edit
```

- Add the following alias section to the config file:

```
[alias]
  use = !sh ~/git-use.sh
```

#### Test the git use Command

Now you can test the script by using the following commands:

- To switch to the DevOps user:

```
git use devops
```

- To switch to the Freelancer user:

```
git use freelancer
```


## Conclusion

By following these steps, you can easily switch between different Git users based on your use case. This solution is ideal for developers working on multiple projects with different identities (e.g., personal vs. freelance vs. other roles) and simplifies the management of Git configurations.
