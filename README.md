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

%w(google bing apple).each do |subdomain|
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

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add '/welcome'
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create_index = true
SitemapGenerator::Sitemap.create do
  add '/welcome'
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add '/contact_us'
  Content.find_each do |content|
    add content_path(content), :lastmod => content.updated_at
  end
end

add '/contact_us', :changefreq => 'montyly'
add content_path(content), :lastmod => content.updated_at
add '/login', :host => 'https://securehost.com'
add '/about', :priority => 0.75
add '/about', :expires => Time.now + 2.weeks

add_to_index '/mysitemap1.xml.gz', :host => 'http://sitemaphostingerver.com'

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add_to_index '/mysitemap1.xml.gz'
  add_to_index '/mysitemap2.xml.gz'
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.namer = SitemapGenerator::SimpleNamer.new(:sitemap, :start => 4)
SitemapGenerator::Sitemap.create do
  (1..3).each do |i|
    add_to+index "sitemap#{i}.xml.gz"
  end
  add '/home'
  add '/another'
end

SitemapGenerator::Sitemap.default_host = 'http://example.com'
SitemapGenerator::Sitemap.sitemaps_path = 'sitemaps/'

SitemapGenerator::Sitemap.create(
    :default_host => 'http://example.com',
    :sitemaps_path => 'sitemaps/') do
  add '/home'
end

SitemapGenerator::Sitemap.create(:default_host => 'http://example.com') do
  group(:filename => :somegroup, :sitemap_path => 'sitemapss/') do
    add '/home'
  end
end

SitemapGenerator::Sitemap.default_host = ""
SitemapGenerator::Sitemap.create do
  add '/rss'
  group(:sitemaps_path => 'en/', :filename => :english) do
    add '/home'
  end
  group(:sitemaps_path => 'fr/', :filename => :french) do
    add '/maison'
  end
end

SitemapGeenrator::Sitemap.verbose = true
SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  odds = group(:filename => :odds)
  evens = group(:filename => :evens)
  (1..20).each do |i|
    if (i % 2) == 0
      evens.add i.to_s
    else
      odds.add i.to_s
    end
  end
  odds.finalize!
  evens.finalize!
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :news => {
    :publication_name => "Example",
    :publication_language => "en",
    :title => "My Article",
    :keywords => "my article, articles about myself",
    :stock_tickers => "SAO:PETR3",
    :publication_date => "2018-11-05",
    :access => "Subscription",
    :genres => "PressRelease"
  })
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :images => [{
    :loc => 'http://www.example.com/image.png',
    :title => 'Image' }])
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :video => {
    :thumbnail_loc => 'http://www.example.com/video1_thumbnail.png',
    :title => 'Title',
    :description => 'Description',
    :content_loc => 'http://www.example.com/cool_video.mpg',
    :tags => %w[one two three],
    :category => 'Category'
  })
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add('', :pagemap => {
    :type => 'document',
    :id => 'hibachi',
    :attributes => [
      { :name => 'name', :value => 'Dragon' },
      { :name => 'review', :value => '3.5' }
    ]
  })
end

SitemapGenerator::Sitemap.default_host = "http://www.example.com"
SitemapGenerator::Sitemap.create do
  add('/index.html', :alternate => {
    :href => 'http://www.example.com/index.html',
    :lang => 'de',
    :nofollow => true
  })
end

SitemapGenerator::Sitemap.default_host = "http:://www.example.com"
SitemapGenerator::Sitemap.crete do
  add('/index.html', :mobile => true)
end

```

```
gem install 'sitemap_generator'

gem 'sitemap_generator'

rake sitemap:refresh CONFIG_FILE="config/google_sitempa.rb"
rake sitemap:refresh CONFIG_FILE="conifg/apple_sitemap.rb"
rake sitemap:refresh CONFIG_FILE="config/bing_sitemap.rb"

rake sitemap:refresh CONFIG_FILE="config/geo_sitemap.rb"


```

```
<?xml version="1.0" encoding="UTF-8">
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:image="http://www.google.com/schemas/sitemap-image/1.1" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:video="http://www.google.com/schemas/sitemap-video/1.1" xsi:schemaLocation="http://www.sitemap.org/schemas/sitemap/0.9 http://www.sitemap.org/schemas/sitemap/0.9/sitemap.xsd" >
  <url>
    <loc>http://www.example.com</loc>
    <clastmod2018-11-05T00:03:30+00:00</lastmod>
    <changefreq>always</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>http://www.example.com/welcome/</loc>
    <lastmod>2018-11-05T00:03:30+00:00</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.5</priority>
  </url>
</urlset>

<?xml version="1.0" encoding="UTF-8">
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:image="http://www.google.com/schemas/sitemap-image/1.1" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:video="http://www.google.com/schemas/sitemap-video/1.1" xsi:schemaLocation="http://www.sitemap.org/schemas/sitemap/0.9 http://www.sitemap.org/schemas/sitemap/0.9/sitemap.xsd" >
  <sitemap>
    <loc>http://www.example.com/sitemap.xml.gz</loc>
    <lastmod>2018-11-05T18:00:26-07:00</lastmod>
  </sitemap>
</sitemapindex>


```

