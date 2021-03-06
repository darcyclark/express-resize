# Tests

## params
 params should return an object with two keys: height, width

```
var req = {
    query: {
        height: 600,
        width: 600
    }
};
var result = util.params(req);
assert.equal(2, Object.keys(result).length);
```


 params should return an object with the keys: height = 600, width = null

```
var req = {
    query: {
        height: 600,
        width: '6dsf00'
    }
};
var result = util.params(req);
assert.equal((Object.keys(result).length == 2),(result.width == null));
```


 params should return an object with the keys: height = null, width = 600

```
var req = {
    query: {
        height: 0,
        width: 600
    }
};
var result = util.params(req);
assert.equal((Object.keys(result).length == 2),(result.height == null));
```


 params should return null

```
var req = {
    query: {}
};
var result = util.params(req);
assert.equal(null, result);
```


## relativePath
 relativePath should return a path without leading slash

```
var path = '/Content/Images/car.jpeg';
var result = util.relativePath(path);
assert.equal(true, (result.charAt(0) !== '/'));
```


## parseReqUrl
 parseReqUrl return an array

```
var path = 'content/image.jpg';
var result = util.parseReqURL(path);
assert.equal("object", typeof(result));
```


 parseReqUrl return an array with two keys

```
var path = 'content/image.jpg';
var result = util.parseReqURL(path);
assert.equal(2, result.length);
```


## assetAvaialble
 assetAvaialble should callback when asset is available

```
var path = 'tests/test.png';
util.assetAvailable(path, function (err) {
    if (err)
        assert.equal(true, false);
    assert.equal(true, true);
});
```


 assetAvaialble should callback with error when asset is unavailable

```
var path = 'tests/test.jpg';
util.assetAvailable(path, function (err) {
    if (err)
        assert.equal(true, false);
    assert.equal(true, true);
});
```
