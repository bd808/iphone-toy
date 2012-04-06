require "rubygems"
require "bundler"

# ensure gems are available
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems."
  exit e.status_code
end

desc "Compiles CoffeeScript using Barrista (but only if they changed)"
task 'coffee:compile' do
  require 'barista'
  abort "'#{Barista::Compiler.bin_path}' is unavailable." unless Barista::Compiler.available?
  Barista.compile_all! false, false
end

desc "Compiles SASS using Compass"
task 'sass:compile' do
  sh 'bundle exec compass compile'
end

namespace :assets do
  desc "Compiles all assets (CSS/JS)"
  task :compile => ['coffee:compile', 'sass:compile']

  desc "Removes all compiled and bundled assets"
  task :clean do
    files = []
    files << ".sass-cache/**"
    files << "assets/css/screen.css"
    files << "assets/css/print.css"
    files << "assets/css/ie.css"
    rm_rf files
  end
end

desc "Compiles and bundles all assets"
task :assets => ['assets:compile']


def ok_failed(condition)
  if (condition)
    puts "OK"
  else
    puts "FAILED"
  end
end

def get_stdin(message)
  print message
  STDIN.gets.chomp
end

def ask(message, valid_options)
  if valid_options
    answer = get_stdin("#{message} #{valid_options.to_s.gsub(/"/, '').gsub(/, /,'/')} ") while !valid_options.include?(answer)
  else
    answer = get_stdin(message)
  end
  answer
end

desc "list tasks"
task :list do
  puts "Tasks: #{(Rake::Task.tasks - [Rake::Task[:list]]).join(', ')}"
    puts "(type rake -T for more detail)\n\n"
end

task :default => ['assets']
