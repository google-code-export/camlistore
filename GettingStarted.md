1) Download the latest release's zip file from:

http://camlistore.org/download

and unzip it.

2) Install:

```
cd camlistore-0.2   (or whatever)
go run make.go
```

3) start the camlistored server:

```
./bin/camlistored
```

At startup, it should generate for you the server configuration file, at:

$HOME/.config/camlistore/server-config.json

and a new secret keyring:

$HOME/.config/camlistore/identity-secring.gpg

containing a new gpg key.

4) use camput to generate a clients configuration file

Startup during the previous step should have already output the gpg key to use in the command below, something like E8168483

```
./bin/camput init --gpgkey <your gpg key>		
```

Your new client configuration file should be at:

$HOME/.config/camlistore/client-config.json

5) get started

Starting the server has most likely opened a new browser window for you. If not, camlistore should be available at http://localhost:3179/ui/