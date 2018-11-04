### SitemapGenerator
---
https://github.com/kjvarga/sitemap_generator

```ruby
require 'sitemap_generator/tasks'

config.gem 'sitemap_generator'

SitemapGenerator.verbose = false

SitemapGenerator::Sitemap.search_engiens

SitemapGenerator::Sitemap.ping_search_engines(newengines: 'http://newengine.com/ping?url=%s')

SitemapGenerator::Sitemap.default_host = 'http://example.com'
SitemapGenerator::Sitemap.ping_search_engines

every 1.day, :at => '5:00 am' do
  rake "-s sitemap:refresh"
end

Sitemap: http://www.example.com/sitemap.xml.gz



```

```
gem install 'sitemap_generator'

gem 'sitemap_generator'


```

```

```

