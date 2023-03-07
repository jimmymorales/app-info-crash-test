# app-info-crash-test

Simple project that reproduces a crash that occures when running the `app_info` lane with an AAB file.

The crash seems to happen after upgrading the Material library (`com.google.android.material:material`) to version `1.7.0` or greater.

## Steps to reproduce
1. Clone repository
1. Run `bundle exec fastlane deploy`

## Notes
1. If you comment [the line where we add Material as a dependency](https://github.com/jimmymorales/app-info-crash-test/blob/main/app/build.gradle#L53) the `deploy` lane will succeed.
2. It works when running `app_info` with a APK.

## Stacktrace
```
bundler: failed to load command: fastlane (/Users/jmorales/.gem/bin/fastlane)
Traceback (most recent call last):
        75: from /Users/jmorales/.gem/bin/bundle:23:in `<main>'
        74: from /Users/jmorales/.gem/bin/bundle:23:in `load'
        73: from /Users/jmorales/.gem/gems/bundler-2.3.22/exe/bundle:36:in `<top (required)>'
        72: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/friendly_errors.rb:120:in `with_friendly_errors'
        71: from /Users/jmorales/.gem/gems/bundler-2.3.22/exe/bundle:48:in `block in <top (required)>'
        70: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/cli.rb:25:in `start'
        69: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/vendor/thor/lib/thor/base.rb:485:in `start'
        68: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/cli.rb:31:in `dispatch'
        67: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/vendor/thor/lib/thor.rb:392:in `dispatch'
        66: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/vendor/thor/lib/thor/invocation.rb:127:in `invoke_command'
        65: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/vendor/thor/lib/thor/command.rb:27:in `run'
        64: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/cli.rb:486:in `exec'
        63: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/cli/exec.rb:23:in `run'
        62: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/cli/exec.rb:58:in `kernel_load'
        61: from /Users/jmorales/.gem/gems/bundler-2.3.22/lib/bundler/cli/exec.rb:58:in `load'
        60: from /Users/jmorales/.gem/bin/fastlane:23:in `<top (required)>'
        59: from /Users/jmorales/.gem/bin/fastlane:23:in `load'
        58: from /Users/jmorales/.gem/gems/fastlane-2.212.1/bin/fastlane:23:in `<top (required)>'
        57: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/cli_tools_distributor.rb:123:in `take_off'
        56: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/commands_generator.rb:43:in `start'
        55: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/commands_generator.rb:354:in `run'
        54: from /Users/jmorales/.gem/gems/commander-4.6.0/lib/commander/delegates.rb:18:in `run!'
        53: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane_core/lib/fastlane_core/ui/fastlane_runner.rb:124:in `run!'
        52: from /Users/jmorales/.gem/gems/commander-4.6.0/lib/commander/runner.rb:444:in `run_active_command'
        51: from /Users/jmorales/.gem/gems/commander-4.6.0/lib/commander/command.rb:157:in `run'
        50: from /Users/jmorales/.gem/gems/commander-4.6.0/lib/commander/command.rb:187:in `call'
        49: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/commands_generator.rb:110:in `block (2 levels) in run'
        48: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/command_line_handler.rb:36:in `handle'
        47: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/lane_manager.rb:47:in `cruise_lane'
        46: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:45:in `execute'
        45: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:45:in `chdir'
        44: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:49:in `block in execute'
        43: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/lane.rb:33:in `call'
        42: from Fastfile:36:in `block (2 levels) in parsing_binding'
        41: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/fast_file.rb:159:in `method_missing'
        40: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:157:in `trigger_action_by_name'
        39: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:229:in `execute_action'
        38: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:229:in `chdir'
        37: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:255:in `block in execute_action'
        36: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/actions/actions_helper.rb:69:in `execute_action'
        35: from /Users/jmorales/.gem/gems/fastlane-2.212.1/fastlane/lib/fastlane/runner.rb:263:in `block (2 levels) in execute_action'
        34: from /Users/jmorales/.gem/gems/fastlane-plugin-app_info-0.7.0/lib/fastlane/plugin/app_info/actions/app_info_action.rb:16:in `run'
        33: from /Users/jmorales/.gem/gems/fastlane-plugin-app_info-0.7.0/lib/fastlane/plugin/app_info/helper/app_info_helper.rb:18:in `raw_data'
        32: from /Users/jmorales/.gem/gems/fastlane-plugin-app_info-0.7.0/lib/fastlane/plugin/app_info/helper/app_info_helper.rb:53:in `common_columns'
        31: from /Users/jmorales/.gem/gems/fastlane-plugin-app_info-0.7.0/lib/fastlane/plugin/app_info/helper/app_info_helper.rb:53:in `each_with_object'
        30: from /Users/jmorales/.gem/gems/fastlane-plugin-app_info-0.7.0/lib/fastlane/plugin/app_info/helper/app_info_helper.rb:53:in `each'
        29: from /Users/jmorales/.gem/gems/fastlane-plugin-app_info-0.7.0/lib/fastlane/plugin/app_info/helper/app_info_helper.rb:54:in `block in common_columns'
        28: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/aab.rb:57:in `name'
        27: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/aab.rb:182:in `manifest'
        26: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/aab.rb:187:in `resource'
        25: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:12:in `parse'
        24: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:12:in `new'
        23: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:20:in `initialize'
        22: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:41:in `parse'
        21: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:46:in `define_packages'
        20: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:46:in `each_with_object'
        19: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:46:in `each'
        18: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:47:in `block in define_packages'
        17: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:47:in `new'
        16: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:62:in `initialize'
        15: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:103:in `define_types'
        14: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:103:in `each'
        13: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:105:in `block in define_types'
        12: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:117:in `parse_from'
        11: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:117:in `each_with_object'
        10: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:117:in `each'
         9: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:118:in `block in parse_from'
         8: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:118:in `new'
         7: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:129:in `initialize'
         6: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:150:in `parse'
         5: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:150:in `each_with_object'
         4: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:150:in `each'
         3: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:151:in `block in parse'
         2: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:151:in `new'
         1: from /Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:166:in `initialize'
/Users/jmorales/.gem/gems/app-info-2.8.3/lib/app_info/protobuf/resources.rb:191:in `parsed_value': \e[31m[!] undefined method `to_sym' for nil:NilClass\e[0m (NoMethodError)
```
