source 'https://rubygems.org'

gem 'rake'

platforms :ruby do
  gem 'sqlite3', '>= 2.10.2'
end

platforms :jruby do
  gem 'activerecord-jdbcsqlite3-adapter'
  gem 'jruby-openssl'
  gem 'mime-types', ['~> 2.6', '< 2.99']

  if ENV['RAILS_VERSION'] == 'edge'
    gem 'railties', :github => 'rails/rails'
  elsif ENV['RAILS_VERSION']
    gem 'railties', "~> #{ENV['RAILS_VERSION']}"
  else
    gem 'railties', ['>= 3.0', '< 9.0']
  end
end

platforms :rbx do
  gem 'psych'
end

group :test do
  if ENV['RAILS_VERSION'] == 'edge'
    gem 'actionmailer', :github => 'rails/rails'
    gem 'activejob',    :github => 'rails/rails'
    gem 'activerecord', :github => 'rails/rails'
  elsif ENV['RAILS_VERSION']
    gem 'actionmailer', "~> #{ENV['RAILS_VERSION']}"
    gem 'activerecord', "~> #{ENV['RAILS_VERSION']}"
  else
    gem 'actionmailer', ['>= 3.0', '< 9.0']
    gem 'activerecord', ['>= 3.0', '< 9.0']
  end
  gem 'net-smtp' if Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.1.0')
  gem 'rspec', '>= 3'
  gem 'simplecov', :require => false
  gem 'simplecov-lcov', :require => false
  if Gem::Version.new(RUBY_VERSION) >= Gem::Version.new('3.3.0')
    # New dependencies with a deprecation notice in Ruby 3.3 and required in Ruby 3.4
    # Probably won't get released in rails 7.0
    gem 'base64'
    gem 'bigdecimal'
    gem 'mutex_m'
    gem 'ostruct'
  end
  if ENV['RAILS_VERSION'].nil? || ENV['RAILS_VERSION'] >= '6.0.0'
    gem 'zeitwerk', :require => false
  end
  gem 'concurrent-ruby'
end

group :rubocop do
  gem 'rubocop', '>= 1.0'
end

gemspec
