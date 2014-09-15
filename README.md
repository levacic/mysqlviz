# mysqlviz fork

This repo is a fork of https://code.google.com/p/mysqlviz/ made so as to fix some minor bugs, and have a personal copy of the project.

The program is meant to be used so as to get a graphical represenation of a MySQL or SQLite database, by converting a database dump file into a `.dot` file, which can then be parsed by `graphviz` to generate images.


## Installation

Just put the `mysqlviz` file in some folder which is in your path, e.g. `$HOME/bin` or whatever. It's already executable so you should be able to run it immediately. You also need to have `graphviz` installed

The recommended usage flow is the following (mostly copied from the original project's README):


### 1. Dump your database

MySQL:

```
$ mysqldump -d db > ./db.sql # -d = 'no data', only structure
```

SQLite:

```
$ sqlite database.db .dump > ./db.sql # SQLite (also: 'sqlite3 ...')
```

### 2. Convert the dump file

```
$ mysqlviz -f ./db.sql > ./db.dot # 'dot' is a graphviz format.
```

### 3. Generate images with graphviz

Run these:

```
$ dot -Tpng ./db.dot > ./db.dot.png
$ fdp -Tpng ./db.dot > ./db.fdp.png
$ circo -Tpng ./db.dot > ./db.circo.png
$ twopi -Tpng ./db.dot > ./db.twopi.png
$ neato -Tpng ./db.dot > ./db.neato.png
```

The commands are sorted in the order that, in my experience, appears to give the best results (from best to worst). Not that `twopi` and `neato` are often unusable because they overlap text, which makes everything unreadable.

## License

The code is licensed under GNU GPL v3, according to the original project page: https://code.google.com/p/mysqlviz/
