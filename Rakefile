require 'spec'
require 'spec/rake/spectask'
require 'rubygems'
require 'rake'
require 'echoe'

def extract_version
    File.open('VERSION').readline.chop
end
Spec::Rake::SpecTask.new(:spec) do |t|
  t.spec_opts ||= []
  t.ruby_opts << "-rrubygems"
  t.ruby_opts << "-Ilib"
  t.ruby_opts << "-rhttp_router"
  t.ruby_opts << "-rspec/spec_helper"
  t.spec_opts << "--options" << "spec/spec.opts"
  t.spec_files = FileList['spec/**/*_spec.rb']
end

Echoe.new('http_router', extract_version) do |p|
    p.description       = "A kick-ass HTTP router for use in Rack & Sinatra" 
    p.url               = "http://github.com/joshbuddy/http_router"  
    p.author            = "Joshua Hull"
    p.email             = "joshbuddy@gmail.com"
    p.development_dependencies = []
end

begin
  require 'code_stats'
  CodeStats::Tasks.new
rescue LoadError
end

require 'rake/rdoctask'
desc "Generate documentation"
Rake::RDocTask.new do |rd|
  rd.main = "README.rdoc"
  rd.rdoc_files.include("README.rdoc", "lib/**/*.rb")
  rd.rdoc_dir = 'rdoc'
end
