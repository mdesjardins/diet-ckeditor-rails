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

# Rakefile in your my_awesome_gem gem

# Monkey patch Bundler gem_helper so we release to our gem server instead of rubygems.org
module Bundler
  class GemHelper
    def rubygem_push(path)
      gem_server_url = 'http://tater:tots2000@scripps-gems.elctech.net'
      sh("gem inabox '#{path}' --host #{gem_server_url}")
      Bundler.ui.confirm "Pushed #{name} #{version} to #{gem_server_url}"
    end
  end
end
