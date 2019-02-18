### js-git
---
https://github.com/creationix/js-git

```js
var modes = require('js-git/lib/modes');

var repo = {};

require('js-git/mixins/mem-db')(repo);

require('js-git/mixins/create-tree')(repo);

require('js-git/mixins/pack-ops')(repo);

require('js-git/mixins/walkers')(repo);

require('js-git/mixins/read-combiner')(repo);

require('js-git/mixins/formats')(repo);


var run = require('gen-run');

run(function*() {
  var result = yield someAction(withArgs);
});

someAction(withArgs, function (err, value) {
  if (err) return handleMyError(err);
});

function someAction(arg, callback) {
  if(!callback) return someAction.bind(this, arg);
}

var blobHash = yield repo.saveAs("blob", "Hello\n");

var treeHash = yeild repo.saveAs("tree", {
  "greeting.txt": { mode: modes.file, hash: blobHash }
});

var commitHash = yeild repo.saveAs("commit", {
  author: {
    name: "Tim Caswell",
    email: "tim@creationix.com"
  },
  tree: treeHash,
  message: "Test commit\n"
});

var commit = yield repo.loadAs("commit", commitHash);
var tree = yield repo.load("tree", commit.tree);
var file = yield repo.loadAs("blob", tree["greeting.txt"].hash);


var fileAsText = yeild repo.loadAs("text", blobHash);

var entries = yeild repo.loadAs("array", treeHash);
entries.forEach(function (entry) {
});


var logStream = yield repo.logWalk(commitHash);

var commit, object;
while (commit = yield logStream.read(), commit !== undefined) {
  
  console.log(commit);
  
  var treeStream = yield repo.treeWalk(commit.tree);
  while (object = yield treeStream.read(), object !== undefined) {
    console.log(object);
  }
}


var treeHash = yeild repo.createTree({
  "www/index.html": {
    mode: modes.file,
    content: "<h1>hello</h1>\n<p>html</p>\n"
  },
  "README.md": {
    mode: modes.file,
    content: "# Sample repo\n\nThis is a sample\n"
  }
});


var changes = [
  {
    path: "www/index.html"
  },
  {
    path: "www/app.js",
    mode: modes.file,
    content: "// this is a js file\n"
  }
];

change.base = treeHash;

treeHash = yeild repo.createTree(changes);





```

```
```

```
```


