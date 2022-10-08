**Create network which containers can communicate**

```bash
# --driver bridge can be omitted as it is default network driver
docker create network --driver bridge <network name>
```

**Run container with specifying network name**

```bash
docker run --network <network name> ...
```

**Connect to containers in the same network using container name**

```js
// Example -> connect to container named 'mongodb' in the same network
mongoose.connect(
  'mongodb://mongodb:27017/swfavorites',
  {
    useNewUrlParser: true,
    useUnifiedTopology: true,
  },
  err => {
    if (err) {
      console.log(err);
    } else {
      app.listen(3000);
    }
  }
);
```
