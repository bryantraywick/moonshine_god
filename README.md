# Moonshine_God

### A plugin for [Moonshine](http://github.com/railsmachine/moonshine)

Moonshine_God provides simple installation and configuration management
for [god](http://god.rubyforge.com). Just drop your god configs into
<tt>config/god/*.god</tt> in your Rails application, add a couple lines to your
Moonshine manifest, and deploy.

Available options:
* <tt>log_level</tt> - One of debug, info, warn, error, or fatal. Default is 'warn'.
* <tt>log_file</tt> - Path to log file. Default is /var/log/god.log.

### Instructions

* <tt>script/plugin install git://github.com/railsmachine/moonshine_god.git</tt>
* Add god configuration files at config/god/*.god
* Configure settings in the manifest if desired:
    configure(
      :god => {
        :log_level => 'info',
        :log_file => "#{configuration[:deploy_to]}/shared/log/god.log"
      }
    )
* Include the plugin and recipe(s) you want to use in your Moonshine manifest.
    recipe :god
* Add the :god role to server(s) in your capistrano deploy file(s) running god:
    # config/deploy/staging.rb
    server 'staging.example.com', :god, :app, :web, :db, :primary => true
    
***

Unless otherwise specified, all content copyright &copy; 2014, [Rails Machine, LLC](http://railsmachine.com)
