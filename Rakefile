require 'rake'
require 'rake/testtask'
require 'rake/clean'

CLEAN.include("**/*.gem", "**/*.rbc")

namespace 'gem' do
  desc 'Create the win32-ipc gem'
  task :create => [:clean] do
    require 'rubygems/package'
    spec = eval(IO.read('win32-ipc.gemspec')) 
    Gem::Package.build(spec)
  end

  desc 'Install the win32-ipc gem'
  task :install => [:create] do
    file = Dir['*.gem'].first
    sh "gem install -l #{file}"
  end
end

Rake::TestTask.new do |t|
  t.verbose = true
  t.warning = true
end

task :default => :test
