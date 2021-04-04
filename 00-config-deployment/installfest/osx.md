# Mac OSX

## SEI Atlanta Install Fest

## PART 1

For the first portion of the class, we'll be working exclusively inside of the browser and Node. We'll be installing the following tools.

* Slack
* Homebrew
* iTerm
* Oh my ZSH
* VS Code
* Git

### Slack

We will be using slack to communicate throughout the course. You should've received an invite to our channels via e-mail. You can login via the web browser, but downloading / installing the app is highly recommended.

[Download Slack](https://slack.com/downloads)

### iTerm

iTerm is a tricked out version of the Terminal app that is the default command line interface for Mac. It will help with the visuals of the command line navigation, especially with ohmyZSH.

[Download here](https://www.iterm2.com/)

### Install Oh My ZSH

Oh my ZSH?!!! We will be tricking out commandline with another shell. A shell is an interface into our computer, and we will be using a lot to run commands.

We'll be using a shell and configuration package called [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh)

Visit the \[iTerm website\] for install instructions. Open iTerm and run the command listed on the site.

If it prompts you to change your default shell to zsh, select yes! When it asks you for your password, enter your computer user password \(it wont show up, but iTerm is keeping track of your keystrokes\).

Restart Terminal, and you should see a brand new and colorful command prompt.

### Homebrew

Homebrew is a package manager that we will use to install various command line tools in our class.

Visit the [homebrew website](https://brew.sh/) for install instructions.

You may be prompted to installed XCode command line tools. When prompted, click and install through that, and you're homebrew installation will continue.

After the installation process, run the command `brew doctor`. If any warnings or errors are displayed, we will need to resolve them before proceeding with the rest of the install fest.

### Xcode

We do not use Xcode in class but some other applications that we do use require some Xcode libraries. Normally, all you need is the Xcode CLI which should have already been installed when you installed Homebrew. If it didn't get installed, you can use this command:

```text
xcode-select --install
```

If you need to, you can install Xcode through the App Store. [Link here](https://itunes.apple.com/us/app/xcode/id497799835?mt=12)

### GIT

Before we do this process, please make sure you have signed up for an account on [Github](http://www.github.com). We will be installing a version of GIT from home brew and also configuring it.

To install GIT

```text
brew install git
```

**Configuring GIT**

Using your email credentials for GIT, run these commands with your user and email configured.

```text
git config --global user.name "YOUR-USERNAME"
git config --global user.email "YOUR-EMAIL-ADDRESS"
git config --global push.default simple
git config --global credential.helper cache
```

**Setting up SSH Key**

You might find your self having to re-authenticate GIT every time you work on your command line. Setup SSH Keys to let Github remember your machine in the future.

* [Github Generating SSH Keys](https://help.github.com/articles/generating-ssh-keys/)

### Install VS Code

Currently the most popular editor according to developer polls. This is Microsoft's free version of Visual Studio.

Download and install VS Code from [here](https://code.visualstudio.com/download)

To be able to open VS Code from any directory, add it to your path inside your ~/.zshrc file:

```bash
export PATH=$PATH:"/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

Save this file and then fully restart your terminal window \(quit and restart.\)

## Part 2

### Node

To install Node

```text
brew install node
```

Verify the installation afterwards by running

```text
node -v
npm -v
```

The above should display without any errors.

To finish up your installation, run this command to allow for global installations of npm tools.

```text
sudo chown -R $USER /usr/local/lib
```

### Postgres

#### Postgres.app

We will be using a relational database called Postgres during our class.

Download and install from [http://postgresapp.com/](http://postgresapp.com/)

If you have successfully configured zsh and sublime or atom, the following command should work.

```text
subl ~/.zshrc
```

-OR-

```text
atom ~/.zshrc
```

Your sublime \(or Atom\) editor will popup with configuration settings, at the bottom of the file append

```text
export PATH=$PATH:/Applications/Postgres.app/Contents/Versions/9.6/bin
```

While we're here, add these two functions and environment variables to make it easier to access, change and refresh our ZSH configuration file in the future. Copy and paste these to the end of the file.

If you plan on using Sublime Text copy this:

```text
export VISUAL=subl
export EDITOR="$VISUAL"

function zedit() {
  subl ~/.zshrc
}

function zrefresh() {
  echo "Refreshing your ZSH configuration."
  source ~/.zshrc
}
```

Otherwise, if you plan on using Atom, copy this instead:

```text
export VISUAL=atom
export EDITOR="$VISUAL"

function zedit() {
  atom ~/.zshrc
}

function zrefresh() {
  echo "Refreshing your ZSH configuration."
  source ~/.zshrc
}
```

Save the file, close Sublime \(or Atom\), and restart your terminal.

Type `which psql` at which point should display

```text
/Applications/Postgres.app/Contents/Versions/9.5/bin/psql
```

#### Install Postgres GUI

We'll be using **Postico**. Install here:

[https://eggerapps.at/postico/](https://eggerapps.at/postico/)

## Part 3

### Installing MongoDB \(Updated 11/2019\)

**Notes:** The name of the free version of MongoDB has changed to `mongodb-community` as of November 2019. Also, the Catalina version of MacOS \(version 10.15\) disallows folders being created at the root of the file system so you must create your MongoDB data folder inside your home folder

```bash
#Install MongoDB
brew install mongodb-community

#make data directory
sudo mkdir -p ~/mongodb-data
```

After creating the data directory in your home folder, it should be marked with your correct ownership permissions but if you find that it is owned by root instead, you can change it to be owned by you with the following commands:

```bash
#get your user name
whoami

#set data directory permissions (replacing USERNAME with the result from whoami above)
sudo chown -R USERNAME:wheel ~/mongodb-data
```

Finally, to tell MongoDB to start using the data directory that you just created, you must start it with the following command:

```bash
mongod --dbpath ~/mongodb-data
```

To make a shortcut for this command, open your ~/.zshrc \(or ~/.bashrc if not using ZSH\) and add this line to the bottom:

```bash
alias mongod="mongod --dbpath ~/mongodb-data"
```

#### Testing the MongoDB server

```text
#Start the MongoDB server
mongod
```

Press `control-c` to stop the server.

#### Install MongoDB GUI

We'll be using **RoboMongo**. Install here:

[https://robomongo.org/](https://robomongo.org/)

## Part 4

### Installing Python 3

Brew is also used to install Python 3. \(Python 2 is already installed on your Mac.\) To install Python 3 without errors, we first need to create a couple directories and change them to be owned by us:

```text
mkdir /usr/local/lib
mkdir /usr/local/Frameworks
whoami
```

Make a note of the username returned from `whoami`. Enter that username in place of USERNAME below:

```text
sudo chown -R USERNAME:wheel /usr/local/lib
sudo chown -R USERNAME:wheel /usr/local/Frameworks
```

If you received no errors from those commands, then use this command to install version 3:

```text
brew install python3
```

You can test the installation by running `python3 --version`.

This should also install `pip3`, a package installer for Python 3. You can verify that it is installed and working by updating it with the following command:

```text
pip3 install --upgrade pip setuptools wheel
```

This should return some normal messages - no errors. Now that `pip3` is working, we can use it to install a useful Python shell:

```text
pip3 install ipython
```

iPython makes it easy to write python code in your terminal. We may not use it a huge amount but it is handy to have around.

### Installing Django

We will also use `pip3` to install Django, a robust back-end server for Python. We will be installing the 2.0.x version:

```text
pip3 install Django
```

