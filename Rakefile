# -*- ruby -*-

require 'rubygems'
require 'rake/testtask'
require 'rake/rdoctask'
require 'rake/gempackagetask'

$:.push 'lib'
require 'thumbnailer'

PKG_NAME    = 'thumbnailer'
PKG_VERSION = ThumbNailer::VERSION

spec = Gem::Specification.new do |s|
  s.name              = PKG_NAME
  s.version           = PKG_VERSION
  s.summary           = 'Make thumbnails from images.'

  s.files             = FileList['README', 'COPY*', 'Rakefile', 'lib/**/*.rb']
  s.requirements     << 'gd2'
  s.requirements     << 'exifr'
  s.test_files        = FileList['test/*.rb']

  s.has_rdoc          = true
  s.rdoc_options     << '--title' << 'ThumbNailer' << '--charset' << 'utf-8'
  s.extra_rdoc_files  = FileList['README', 'COPYING']

  s.author            = 'Peter Hickman'
  s.email             = 'peterhi@ntlworld.com'

  s.homepage          = 'http://thumbnailer.rubyforge.org'
  s.rubyforge_project = 'thumbnailer'
end

Rake::GemPackageTask.new(spec) do |pkg|
  pkg.need_tar = true
end

desc "Run all the tests"
Rake::TestTask.new("test") do |t|
  t.pattern = 'test/*.rb'
  t.verbose = false
  t.warning = true
end

desc 'Generate API Documentation'
Rake::RDocTask.new('rdoc') do |rdoc| 
  rdoc.rdoc_dir = 'web/doc'
  rdoc.rdoc_files.include('lib/*.rb')  
  rdoc.options << "--all"
end
