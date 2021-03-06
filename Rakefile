# frozen_string_literal: true

require 'cookstyle'
require 'foodcritic'
require 'rake/dsl_definition'
require 'rspec/core/rake_task'
require 'rubocop/rake_task'

desc 'Run RuboCop style and lint checks'
RuboCop::RakeTask.new(:rubocop)

desc 'Run Foodcritic lint checks'
FoodCritic::Rake::LintTask.new(:foodcritic) do |t|
  t.options = {
    tags: %w(~FC022 ~FC122),
    fail_tags: ['any'],
    # include_rules: '',
    context: true,
  }
end

desc 'Run ChefSpec unit tests'
RSpec::Core::RakeTask.new(:spec) do |t|
  t.pattern    = 'test/unit/**/*_spec.rb'
  t.rspec_opts = ' --require ./test/unit/default/chefspec/spec_helper.rb'
end

desc 'Run all tests'
task :style   => %I(rubocop foodcritic)
task :test    => %I(style spec)
task :default => :test
