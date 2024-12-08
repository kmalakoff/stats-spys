## fs-stats-spys

Helper for using sinon spys with fs.Stats.

```
var assert = require('assert');
var statsSpys = require('fs-stats-spys');
var Iterator = require('fs-iterator');

var spys = statsSpys();

var iterator = new Iterator(TEST_DIR);
iterator.forEach(
  function (entry) {
    spys(entry.stats);
  },
  function (err) {
    assert.ok(!err, err ? err.message : '');
    assert.equal(spys.dir.callCount, 5);
    assert.equal(spys.file.callCount, 7);
    assert.equal(spys.link.callCount, 0);
    done();
  }
);
});

```
