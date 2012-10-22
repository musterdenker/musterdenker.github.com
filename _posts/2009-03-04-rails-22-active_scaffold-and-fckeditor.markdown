--- 
layout: post
title: Rails 2.2, Active_Scaffold and FCKEditor
wordpress_id: 92
wordpress_url: http://www.musterdenker.de/?p=92
date: 2009-03-04 14:36:43 +01:00
---
In one of our upcomming Projects we are using Active_Scaffold for Backend Functionality. Therefore we want to integrate the FCKEditor. We are using the actual Version of the <a href="http://rubyforge.org/projects/fckeditorp/" target="_blank">FCKEditor Plugin</a> for Rails.  To integrate the FCKEditor with Active_Scaffold i was following this <a href="http://ganeshmohan.wordpress.com/2008/11/12/fck-editor-plugin-in-activescaffold/" target="_blank">Tutorial</a>. But it seems that this  does not run with Rails 2.2.

We´ve got the following error:
<pre lang="ruby">NoMethodError (undefined method `configure' for #):
    /vendor/plugins/active_scaffold/lib/active_scaffold/config/core.rb:147:in `method_missing'
    /vendor/plugins/active_scaffold/lib/active_scaffold.rb:57:in `active_scaffold'</pre>
This was happen right after the instgallation of the FCKEditor Pugin so i was diggin deeper into the Problem. It comes out that the problem was the overwrite of the <strong>javascript_include_tag</strong> in the fckeditor.rb. My solution was to comment the hole module out.
<pre lang="ruby"># Fckeditor
module Fckeditor
  PLUGIN_NAME = 'fckeditor'
  PLUGIN_PATH = "#{RAILS_ROOT}/vendor/plugins/#{PLUGIN_NAME}"
  PLUGIN_PUBLIC_PATH = "#{PLUGIN_PATH}/public"
  PLUGIN_CONTROLLER_PATH = "#{PLUGIN_PATH}/app/controllers"
  PLUGIN_VIEWS_PATH = "#{PLUGIN_PATH}/app/views"
  PLUGIN_HELPER_PATH = "#{PLUGIN_PATH}/app/helpers"

  module Helper
    def fckeditor_textarea(object, field, options = {})
      var = instance_variable_get("@#{object}")
      if var
        value = var.send(field.to_sym)
        value = value.nil? ? "" : value
      else
        value = ""
        klass = "#{object}".camelcase.constantize
        instance_variable_set("@#{object}", eval("#{klass}.new()"))
      end
      id = fckeditor_element_id(object, field)

      cols = options[:cols].nil? ? '' : "cols='"+options[:cols]+"'"
      rows = options[:rows].nil? ? '' : "rows='"+options[:rows]+"'"

      width = options[:width].nil? ? '100%' : options[:width]
      height = options[:height].nil? ? '100%' : options[:height]

      toolbarSet = options[:toolbarSet].nil? ? 'Default' : options[:toolbarSet]

      if options[:ajax]
        inputs = "
<input id="#{id}_hidden" name="#{object}[#{field}]" type="hidden" />\n" &lt;&lt;
                 "<textarea id="#{id}" name="#{id}">#{value}</textarea>\n"
      else
        inputs = "<textarea id="#{id}" name="#{object}[#{field}]">#{value}</textarea>\n"
      end

      js_path = "#{ActionController::Base.relative_url_root}/javascripts"
      base_path = "#{js_path}/fckeditor/"
      return inputs &lt;&lt;
        javascript_tag("var oFCKeditor = new FCKeditor('#{id}', '#{width}', '#{height}', '#{toolbarSet}');\n" &lt;&lt;
                       "oFCKeditor.BasePath = \"#{base_path}\"\n" &lt;&lt;
                       "oFCKeditor.Config['CustomConfigurationsPath'] = '#{js_path}/fckcustom.js';\n" &lt;&lt;
                       "oFCKeditor.ReplaceTextarea();\n")
    end

    def fckeditor_form_remote_tag(options = {})
      editors = options[:editors]
      before = ""
      editors.keys.each do |e|
        editors[e].each do |f|
          before += fckeditor_before_js(e, f)
        end
      end
      options[:before] = options[:before].nil? ? before : before + options[:before]
      form_remote_tag(options)
    end

    def fckeditor_remote_form_for(object_name, *args, &amp;proc)
      options = args.last.is_a?(Hash) ? args.pop : {}
      concat(fckeditor_form_remote_tag(options), proc.binding)
      fields_for(object_name, *(args &lt;&lt; options), &amp;proc)
      concat('

', proc.binding)
    end
    alias_method :fckeditor_form_remote_for, :fckeditor_remote_form_for

    def fckeditor_element_id(object, field)
      id = eval("@#{object}.id")
      "#{object}_#{id}_#{field}_editor"
    end

    def fckeditor_div_id(object, field)
      id = eval("@#{object}.id")
      "div-#{object}-#{id}-#{field}-editor"
    end

    def fckeditor_before_js(object, field)
      id = fckeditor_element_id(object, field)
      "var oEditor = FCKeditorAPI.GetInstance('"+id+"'); document.getElementById('"+id+"_hidden').value = oEditor.GetXHTML();"
    end
  end
end

#include ActionView
#module ActionView::Helpers::AssetTagHelper
#  alias_method :rails_javascript_include_tag, :javascript_include_tag
#
#  #  &lt;%= javascript_include_tag :defaults, :fckeditor %&gt;
#  def javascript_include_tag(*sources)
#    main_sources, application_source = [], []
#    if sources.include?(:fckeditor)
#      sources.delete(:fckeditor)
#      sources.push('fckeditor/fckeditor')
#    end
#    unless sources.empty?
#      main_sources = rails_javascript_include_tag(*sources).split("\n")
#      application_source = main_sources.pop if main_sources.last.include?('application.js')
#    end
#    [main_sources.join("\n"), application_source].join("\n")
#  end
#end</pre>
The second Step was to include the needed Javascript Files on top of our layout file:
<pre lang="ruby">
    <%= javascript_include_tag "fckeditor/fckeditor" %>
    <%= javascript_include_tag "fckcustom" %></pre>
Now the FCKEditor works smoothly with Active_Scaffold. We will show the rest of the Integration with Active_Scaffold in one of our next Posts.
