
```
# test setup for camlibot before deploying it
cd $GOPATH/src/camlistore.org
git pull
mkdir /tmp/camlibot-cache
cd /tmp/camlibot-cache
git clone $GOPATH/src/camlistore.org

mkdir ~/buildbot
cd ~/buildbot
cp $GOPATH/src/camlistore.org/misc/buildbot/bot.go .
# hack some changes to bot.go
go build -o camlibot bot.go
./camlibot -verbose -gotip $HOME/go

# then you can easily cd into $GOPATH/src/camlistore.org and make a breaking commit
# to test if the bot picks on it correctly.
# and subsequently fix the breakage and check that the bot sees it too.

# When satisfied with the bot code:
rm -rf /tmp/camlibot-cache
./camlibot -verbose -gotip $HOME/go
```