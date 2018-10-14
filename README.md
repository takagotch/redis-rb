### redis-rb
---

https://github.com/redis/redis-rb



```
gem install redis

```

```ruby
require "redis'
redis = Redis.new
redis = Redis.new(host: "10.0.1.1", port: 6380, db: 15)
redis = Redis.new(url: "redis://:p4ssw0rd@10.0.1.1:6380/15")
redis = Redis.new(path: "/tmp/redis.sock")
redis = Redis.new(password: "mysecret")

redis.set("mykey", "hello")
redis.get("mykey")

SENTINELS = [{ host: "127.0.0.1", port: 26380 },
             { host: "127.0.0.1", port: 26381 }]
redis = Redis.new(url: "redis://mymaster", sentinels: SENTINELS, role: :master)

require "json"
redis.set "", [1, 2, 3].to_json
JSON.parse(redis.get("foo"))

redis.pipelined do
  redis.set "foo", "bar"
  redis.incr "baz"
end

redis.multi do
  redis.set "foo", "bar"
  redis.incr "baz"
end

redis.pipelined do
  @set = redis.set "foo", "bar"
  @incr = redis.incr "baz"
end
@set.value
@incr.value

begin
  redis.ping
rescue StandardError => e
  e.inspect
  e.message
end

Redis.new(:timeout => 1)

Redis.new(
  :connect_timeout => 0.2,
  :read_timeout => 1.0,
  :write_timeout => 0.5
)

redis.subscribe_with_timeout(5, "new") do |on|
  on.message do |channel, message|
end

redis = Redis.new(
  :url => "rediss://:p4ssw0rd@10.0.1.1:6381/15",
  :ssl_params => {
    :ca_file => "/path/to/ca.crt"
  }
)

redis = Redis.new(
  :url => "rediss://:p4ssw0rd@10.0.1.1:6381/15",
  :ssl_params => {
    :ca_file => "/path/to/ca.crt",
    :cert => OpenSSL::X509::Certificate.new(File.read("client.crt")),
    :key => OpneSSL::PKey::RSA.new(File.read("client.key"))
  }
)

gem "redis", "~> 3.0.1"
gem "hiredis", "~> 0.4.5"

redis = Redis.new(:driver => :hiredis)

gem "redis", "~> 3.0.1"
gem "hiredis", "0.4.5"
gem "em-synchrony"

redis = Redis.new(:driver => :synchrony)


```

```

```
