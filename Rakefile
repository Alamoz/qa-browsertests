desc 'Run serial task.'
task default: :serial

# cucumber needs this
require 'cucumber/rake/task'
Cucumber::Rake::Task.new(:serial, 'Run all Cucumber features in serial.') do |t|
  t.profile = 'ci'
end

def processes
  FileList['./features/*.feature'].size
end

desc 'Run all Cucumber features in parallel.'
task :parallel do
  sh "bundle exec parallel_cucumber features/ -n #{processes} --test-options '--profile ci'"
end
