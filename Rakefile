require "bundler"

Bundler::GemHelper.install_tasks name: "mixlib-shellout"

begin
  require "rspec/core/rake_task"
  RSpec::Core::RakeTask.new do |t|
    t.pattern = "spec/**/*_spec.rb"
  end
rescue LoadError
  desc "rspec is not installed, this task is disabled"
  task :spec do
    abort "rspec is not installed. bundle install first to make sure all dependencies are installed."
  end
end

begin
  require "chefstyle"
  require "rubocop/rake_task"
  desc "Run Chefstyle tests"
  RuboCop::RakeTask.new(:style) do |task|
    task.options += ["--display-cop-names", "--no-color"]
  end
rescue LoadError
  puts "chefstyle gem is not installed. bundle install first to make sure all dependencies are installed."
end

task :console do
  require "irb"
  require "irb/completion"
  require "mixlib/shellout"
  ARGV.clear
  IRB.start
end

task default: %i{spec style}
