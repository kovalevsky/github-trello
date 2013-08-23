require "bundler"
Bundler.setup

require "rake"
require "rspec"
require "rspec/core/rake_task"

RSpec::Core::RakeTask.new("spec") do |spec|
  spec.pattern = "spec/**/*_spec.rb"
end

task :default => :spec

desc "Run Sinatra server"
task :server do
  $LOAD_PATH.unshift File.expand_path(File.dirname(__FILE__) + "/../lib")
  require "yaml"
  require "github-trello/server"

  cfg_path = "/Users/sk/.vegas/trello_web/trello.yml"
  GithubTrello::Server.config = YAML::load(File.read(cfg_path))
  GithubTrello::Server.run! port: ENV['port']
end
