# CKEditor for rails asset pipeline

[CKEditor](http://ckeditor.com/) is a library for WYSIWYG editor to be used inside web pages.

The `diet_ckeditor_rails` gem integrates the `CKEditor` with the Rails asset pipeline. It is
based on Tse-Ching Ho's `ckeditor_rails` plugin. This gem removes all languages except english,
removes all styles except v2, and removes a few extra plugins. Instructions at the end of
this README tell you how you can create your own custom barebones ckeditor gem. By eliminating
files you don't need, you can reduce the amount of time spent in precompilation.

## Usage

### Install diet_ckeditor_rails gem

Include `diet_ckeditor_rails` in Gemfile

    gem 'diet_ckeditor_rails', :require => 'diet-ckeditor-rails'

Then run `bundle install`

### Include CKEditor javascript assets

Add to your `app/assets/stylesheets/application.js` after `//= require jquery_ujs` to work with jQuery

    //= require ckeditor-jquery

### Modify form field for CKEditor

Add `ckeditor` class to text area tag

    <%= f.text_area :content, :class => 'ckeditor' %>

### Include customized configuration javascript for CKEditor

Add your `app/assets/javascripts/ckeditor/config.js.coffee` like

    CKEDITOR.editorConfig = (config) ->
      config.language = "zh"
      config.uiColor = "#AADC6E"
      true

### Include customized stylesheet for contents of CKEditor

Add your `app/assets/stylesheets/ckeditor/contents.css.scss` like

    body {
      font-size: 14px;
      color: gray;
      background-color: yellow;
    }
    ol,ul,dl {
      *margin-right:0px;
      padding:4 20px;
    }

## Gem maintainance

Maintain `diet_ckeditor_rails` gem with `Rake` commands.

Update origin CKEditor source files.

    rake update-diet-ckeditor VERSION=3.6.3

Publish gem.

    rake release

## License

CKEditor use [CKEditor license](http://ckeditor.com/license).

Other parts of gem use MIT license.
