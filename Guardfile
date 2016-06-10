# A sample Guardfile
# More info at https://github.com/guard/guard#readme

## Uncomment and set this to only include directories you want to watch
# directories %w(app lib config test spec features) \
#  .select{|d| Dir.exists?(d) ? d : UI.warning("Directory #{d} does not exist")}

## Note: if you are using the `directories` clause above and you are not
## watching the project directory ('.'), then you will want to move
## the Guardfile to a watched dir and symlink it back, e.g.
#
#  $ mkdir config
#  $ mv Guardfile config/
#  $ ln -s config/Guardfile .
#
# and, you'll have to watch "config/Guardfile" instead of "Guardfile"

# Add files and commands to this file, like the example:
#   watch(%r{file/path}) { `command(s)` }
#
directories %w(views) \
  .select { |d| Dir.exist?(d) ? d : UI.warning("Directory #{d} does not exist") }

guard :shell do
  watch /.*\.slim$/ do |modified_files|
    file = modified_files[0].gsub(/\.slim$/, '.html').gsub(/^views/, 'draft')
    puts "Updated #{file}"
    `slim_data="$(cat options.json)"; slimrb -p -l "${slim_data}"  #{modified_files[0]} > #{file}`
  end
end

# puts "1: #{modified_files[0]}"
# `tail #{modified_files[0]}`
# slim_data = JSON.parse(File.read('options.json'))
# slim_data = File.read('options.json').to_s
# puts "json: #{slim_data.to_s}"
# `slimrb -p -l "#{slim_data}" #{modified_files[0]} > #{file}`