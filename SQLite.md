# SQLite support #

How to build Camlistore with sqlite support.

Note that using SQLite is optional.  You can also use Camlistore's built-in "kv" pure-Go key/value database, or MySQL, SQLite, Mongo, etc

But assuming you want to use SQLite...

# Dependencies #

## On Debian/Ubuntu ##

```
   $ apt-get install libsqlite3-dev
```

## On OS X ##

```
   $ brew install sqlite3 pkg-config
```

## On Windows ##

?? Kind of a pain.  See http://camlistore.org/docs/server-config#windows

# With `go run make.go` (Recommended) #

Most users should build Camlistore with `go run make.go`, which will automatically use SQLite if it's available.

To force it, use:

```
    $ go run make.go --sqlite=yes
```

# With the `go` command directly (for Go developers) #

SQLite support is only compiled if the `with_sqlite` tag is specified.

So:

```
   $ go install -v -tags=with_sqlite camlistore.org/server/camlistored
```

If you already have it installed without SQLite, you might need to force it with the `-a` flag:

```
   $ go install -a -v -tags=with_sqlite camlistore.org/server/camlistored
```

This of couse assumes you have your `$GOPATH` set.  If you don't know what that means, use the `go run make.go` option above instead.