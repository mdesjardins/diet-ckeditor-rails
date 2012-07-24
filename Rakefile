#!/usr/bin/env rake
require "bundler/gem_tasks"
require File.expand_path('../lib/ckeditor-rails/source_file', __FILE__)

desc "Update CKEditor Library, VERSION is required."
task "update-diet-ckeditor" do
  files = SourceFile.new
  files.fetch ENV['VERSION']
  files.move
  files.fix_css
  files.fix_js
  files.remove_unwanted_files(ENV.fetch('KEEP_LANGUAGE','en'), ENV.fetch('KEEP_SKIN','v2'), ENV.fetch('REMOVE_PLUGINS','adobeair,devtools,flash'))
  files.cleanup
end
