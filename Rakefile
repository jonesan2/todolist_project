require 'rake/testtask'
require 'find'
require 'bundler/gem_tasks'

desc 'Say hello'
task :hello do
  puts "Hello there. This is the 'hello' task."
end

=begin # simple way of running tests; avoid due to need for regular updating
desc 'Run tests'
task :test do
  sh 'ruby ./test/todolist_project_test.rb'
end
=end

desc 'Run tests'
task :default => :test

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList['test/**/*_test.rb']
end

desc "Display inventory of all files that don't begin with '.'"
task :inventory do
  Find.find('.') do |name|
    next if name.include?('/.') # Excludes files & directories starting with '.' 
    puts name if File.file?(name)
  end
end

=begin # This does the same thing as the inventory task above, but prints the
       # entire directory path.
desc 'List Files'
task :list do
  output = []
  Find.find("/home/ec2-user/environment/todolist_project") do |path|
    if FileTest.directory?(path)
      if File.basename(path).start_with?('.')
        Find.prune # Don't look any further
      else
        next
      end
    else
      if FileTest.file?(path)
        if File.basename(path).start_with?('.')
          Find.prune
        else
          output << path
        end
      end
    end
  end
  puts output
end
=end
  

