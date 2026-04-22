source "https://rubygems.org"

# GitHub Pages 使用的 Jekyll 版本由 github-pages gem 锁定，保持与线上环境一致。
# Use the github-pages gem so local builds match GitHub Pages' pinned Jekyll version.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Windows 与 JRuby 下的时区依赖 / tzinfo dependencies for Windows and JRuby
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# 在 Windows 上使 Jekyll 的文件监听正常工作 / performance booster for watching files on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Ruby 3.0+ 需要显式引入 webrick / webrick is needed on Ruby 3.0+
gem "webrick", "~> 1.8"
