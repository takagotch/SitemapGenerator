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

# robts.txt
# Sitemap: http://www.example.com/sitemap.xml.gz
# Sitemap: http://s3.amazonaws.com/sitemap.generator/sitemap/sitemap.xml.gz

SitemapGenerator::Interpreter.send :include, RoutingHelper

require 'capistrano/sitemap_generator'
set :sitemap_roles, :web

sitemap:create
sitemap:refresh
sitemap:clean

SitemapGenerator::Sitemap.sitemaps_path = 'shared/'

SitemapGenerator::Sitemap.create_index = true
SitemapGenerator::Sitemap.create_index = false
SitemapGenerator::Sitemap.create_index = :auto

SitemapGenerator::Sitemap.adapter = SitemapGenerator::AwsSdkAdapter.new('s3_bucket',
  aws_access_key_id: 'XXXXXXXXXXXX',
  aws_secret_access_key: 'xxxxxxxxxx',
  aws_region: 'us-east-1'
)

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.sitemaps_host = "http://s3.amazonaws.com/sitemap-generator/"
SitemapGenerator::Sitemap.public_path = 'tmp/'
SitemapGenerator::Sitemap.sitemaps_path = 'sitemaps/'
SitemapGenerator::Sitemap.adapter = SitemapGenerator::WaveAdapter.new

%w().each do |subdomain|
  SitemapGenerator::Sitemap.default_host = "http://#{subdomain}.mysite.com"
  SitemapGenerator::Sitemap.sitemaps_path = "sitemaps/#{subdomain}"
  SitemapGenerator::Sitemap.create do
    add '/home'
  end
end

# config/google_sitemap.rb
SitemapGenerator::Sitempa.default_host = "https://google.mysite.com"
SitemapGenerator::SItemap.sitemaps_path = "sitemaps/google"
SitemapGenerator::Sitemap.create do
  add '/home'
end

SitemapGenerator::Sitempa.default_host = "https://apple.mysite.com"
SitempaGenerator::Sitemap.sitemaps_paht = "sitemaps/apple"
SitemapGenerator::Sitemap.create do
  add 'home'
end

SitemapGenerator::Sitemap.default_host = "http://bing.mysite.com"
SitemapGenerator::Sitemap.sitemaps_path = "sitemaps/bing"
SitemapGenerator::Sitemap.create do
  add '/home'
end
```

```
gem install 'sitemap_generator'

gem 'sitemap_generator'


```

```

```

