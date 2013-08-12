# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require File.expand_path('../config/application', __FILE__)

ScalarmInformationService::Application.load_tasks

require 'yaml'

namespace :service do
  desc 'Start the service'
  task :start => :environment do
    config = YAML::load(File.open('config/scalarm.yml'))

    %x[thin start -d --ssl --ssl-verify --ssl-key-file #{config['key_path']} --ssl-cert-file #{config['cert_path']} -p #{config['port']} -C config/thin.yml]
  end

  desc 'Stop the service'
  task :stop => :environment do
    %x[thin stop -C config/thin.yml]
  end

end
