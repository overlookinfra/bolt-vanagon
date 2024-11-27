source 'https://rubygems.org'

def location_for(place)
  if place =~ /^(git[:@][^#]*)#(.*)/
    [{ :git => $1, :branch => $2, :require => false }]
  elsif place =~ /^file:\/\/(.*)/
    ['>= 0', { :path => File.expand_path($1), :require => false }]
  elsif place =~ /(\d+\.\d+\.\d+)/
    [ place, { :require => false }]
  end
end

gem "beaker-hostgenerator", *location_for(ENV['BEAKER_HOSTGENERATOR_VERSION'] || "~> 0.7")
gem "beaker-abs", *location_for(ENV['BEAKER_ABS_VERSION'] || "~> 0.1")
# We must do this here in the plumbing branch so that when the build script
# runs with VANAGON_LOCATION set, it already has the right gem installed.
# Bundler seems to get confused when the rake tasks runs with a different
# vanagon version in the bundle.
gem 'vanagon', *location_for("git@github.com:overlookinfra/vanagon#main")
gem 'packaging', *location_for(ENV['PACKAGING_LOCATION'] || '~> 0.105')
gem 'json'
gem 'rake'
