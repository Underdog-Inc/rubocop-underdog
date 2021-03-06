# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) { |repo_name| "https://github.com/#{repo_name}" }

gemspec

gem "rake", "~> 13.0"

gem "rspec", "~> 3.0"

ruby_version = Gem::Version.new(RUBY_VERSION)
minimum_version = ->(version, engine = "ruby") { ruby_version >= Gem::Version.new(version) && RUBY_ENGINE == engine }
coverage = minimum_version.call("3.1")
linting = minimum_version.call("3.1")
debugging = minimum_version.call("3.1")

gem "pry", platforms: %i[mri jruby]

platforms :mri do
  if linting
    gem "rubocop-md", "~> 1.0", require: false
    gem "rubocop-packaging", "~> 0.5", require: false
    gem "rubocop-performance", "~> 1.11", require: false
    gem "rubocop-rake", "~> 0.6", require: false
    gem "rubocop-rspec", require: false
    gem "rubocop-thread_safety", "~> 0.4", require: false
  end
  if coverage
    gem "codecov", "~> 0.6"
    gem "simplecov", "~> 0.21", require: false
    gem "simplecov-cobertura" # XML for Jenkins
    gem "simplecov-lcov", "~> 0.8", require: false
  end
  if debugging
    # Add `byebug` to your code where you want to drop to REPL
    gem "byebug"
    gem "pry-byebug"
  end
end

platforms :jruby do
  # Add `binding.pry` to your code where you want to drop to REPL
  gem "pry-debugger-jruby"
end
