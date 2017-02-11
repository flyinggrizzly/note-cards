---
title: Creating a Gem
date: 2017-02-08
category: ruby
tags: [ruby, gem, how-to, gem-spec]
description: "Short rundown on writing a gem for Ruby. Includes links to step-by-step instructions from RubyGems and Digital Ocean. Also includes information on using Bundler to make the whole thing easier."
references:
            - http://guides.rubygems.org/make-your-own-gem/
            - https://www.digitalocean.com/community/tutorials/how-to-package-and-distribute-ruby-applications-as-a-gem-using-rubygems
---

## Basics for creating a Gem, according to the [Rubygems.org](http://guides.rubygems.org/make-your-own-gem/) docs

Fundamentally, you need two files:

- `gemname.gemspec`
- `lib/gemname.rb`

The gemspec contains all the information needed to build the gem, including versioning, license, contact info, and the name of the first file to load up (spoiler, it's gonna be `lib/gemname.rb`, which will load all the other bits as the gem is built).

### Template gemspec for a gem called `shrug`

```ruby
Gem::Specification.new do |spec|
  spec.name               = "shrug"
  spec.version            = '0.0.1'
  spec.date               = '2017-02-02'
  spec.authors            = ["Sean DMR"]
  spec.email              = ["sn@grz.li"]
  spec.summary            = %q{Outputs the ¯\_(ツ)_/¯ string}
  spec.description        = %q{No really, that's all it does. Outputs the ¯\_(ツ)_/¯ string.}
  spec.homepage           = "https://flyinggrizzly.io"
  spec.license            = "MIT"

  spec.files              = ['lib/shrug.rb']
  # spec.executables        = ['bin/shrug']
  # spec.test_files         = ['tests/test_shrug.rb']
  # spec.require_paths      = ["lib"]
end
```

It's just ruby, so later on you can script shit in and out of this. Cool.

## To do:

- Write your code, test it.
- Write the gemspec.
- Build the gem (`gem build [gem-name].gemspec`)
- Install the gem from local (`gem install [gemname]-[version].gem`)
- Optional: publish to Rubygems.org (`gem push [gemname]-[version].gem`)

## Advanced: Use Bundler!

Bundler will scaffold your gem directory way better than you can, as well as set up gemspec scripting with `rake`. If you do this, installing and pushing the gem gets a lot easier.

- `rake build # => builds the current version of the gem, also commits everything to Github`
- `rake install # => installs the local gem`
- `rake release # => pushes the thing up to RubyGems`

More detail in a [Digital Ocean guide](https://www.digitalocean.com/community/tutorials/how-to-package-and-distribute-ruby-applications-as-a-gem-using-rubygems).
