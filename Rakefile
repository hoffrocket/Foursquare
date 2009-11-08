require 'rubygems' unless ENV['NO_RUBYGEMS']
require 'rake/gempackagetask'
require 'rubygems/specification'
require 'date'
require 'spec/rake/spectask'

spec = Gem::Specification.new do |s|
  s.name = "foursquare"
  s.version = "0.0.2"
  s.author = "Jeremy Welch"
  s.email = "hello@jeremyrwelch.com"
  s.homepage = "http://foursquare.rubyforge.org"
  s.description = s.summary = "A simple Ruby wrapper for the Foursquare API"
  
  s.platform = Gem::Platform::RUBY
  s.has_rdoc = true
  s.extra_rdoc_files = ["README.rdoc", "LICENSE", "History"]
  
  s.require_path = 'lib'
  s.autorequire = 'foursquare'
  s.files = %w(LICENSE README.rdoc Rakefile History) + Dir.glob("{lib,spec,script,examples}/**/*")
  
  s.add_dependency('httparty', '0.4.3')
end

task :default => :spec

desc "Run specs"
Spec::Rake::SpecTask.new do |t|
  t.spec_files = FileList['spec/**/*_spec.rb']
  t.spec_opts = %w(-fs --color)
end


Rake::GemPackageTask.new(spec) do |pkg|
  pkg.gem_spec = spec
end

desc "install the gem locally"
task :install => [:package] do
  sh %{sudo gem install pkg/#{GEM}-#{GEM_VERSION}}
end

desc "create a gemspec file"
task :make_spec do
  File.open("foursquare.gemspec", "w") do |file|
    file.puts spec.to_ruby
  end
end