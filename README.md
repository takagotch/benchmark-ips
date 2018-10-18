### benchmark-ips
---

https://github.com/evanphx/benchmark-ips

```
gem install kalibera
gem install benchmark-ips
rake newb

```

```ruby
require 'benchmark/ips'
Benchmark.ips do |x|
  x.config(:time => 5, :warmup => 2)
  x.time = 5
  x.warmup = 2
  x.report("addition"){ 1 + 2 }
  x.report("addition2") do |times|
    i = 0
    while i < times
      1 + 2
      i += 1
    end
  end
  x.report("addition3", "1 + 2")
  x.report("addition-rest-long-label") { 1 + 2 }
  x.compare!
end

require 'benchmark/ips'
class GCSuite
  def warming(*)
    run_gc
  end
  def running(*)
    run_gc
  end
  def warmup_stats(*)
  end
  private
  def run_gc
    GC.enable
    GC.start
    GC.disable
  end
end
suite = GCSuite.new
Benchmark.ips do |x|
  x.config(:suite => suite)
  x.report("job1"){ ... }
  x.report("job2"){ ... }
end

Benchmark.ips do |x|
  x.hold! 'filename'
end

Benchmark.ips do |x|
  x.config(:iterations => 3)
  x.iterations = 3
end

Benchmark.ips do |x|
  x.config(:stats => :bootstrap, :confidence => 95)
  x.stats = :bootstrap
  x.confidence = 95
end




```

