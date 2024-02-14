[![rake](https://github.com/yegor256/jekyll-git-hash/actions/workflows/rake.yml/badge.svg)](https://github.com/yegor256/jekyll-git-hash/actions/workflows/rake.yml)
[![Gem Version](https://badge.fury.io/rb/jekyll-git-hash.svg)](http://badge.fury.io/rb/jekyll-git-hash)

I use this plugin in [my Jekyll-powered blog](https://github.com/yegor256/blog).

Install it first:

```
gem install jekyll-git-hash
```

With Jekyll 2, simply add the gem to your `_config.yml` gems list:

```yaml
gems: ['jekyll-git-hash', ... your other plugins]
```

Or for previous versions,
create a plugin file within your Jekyll project's `_plugins` directory:

```ruby
# _plugins/jekyll-git-hash.rb
require 'jekyll-git-hash'
```

Highly recommend to use Bundler. If you're using it, add this line
to your `Gemfile`:

```
gem "jekyll-git-hash"
```

The plugin is compatible with 
[Jekyll 3.9.3](https://jekyllrb.com/news/2023/01/29/jekyll-3-9-3-released/) and 
[Jekyll 4.3.2](https://jekyllrb.com/news/2023/01/20/jekyll-4-3-2-released/). 

Use `{{ site.data['hash']}}` inside your liquid template.

When the site is being generated by Jekyll, the
plugin retrieves Git hash of the source code and
exposes it as a item in `site.data`. This feature
is very helpful when you want your static resources (CSS, JS, etc.)
be reloaded by end users every time you deploy a new
version of the site.

For example, in your `default.html`:

```html
<link rel="stylesheet" href="/css/layout.css?{{ site.data['hash'] }}"/>
```

The URL will be generated with a suffix at the end. This
suffix doesn't change the URL (`layout.css` will still
be accesible by the browser), but it makes the URL unique
for the browser when you deploy a new Git revision. All browsers
will reload this CSS.

