require 'pathname'

root_dir = Pathname.new(__FILE__).dirname
integration_test_dir = root_dir + 'test' + 'integration'
integration_test_dirs = Pathname.new(integration_test_dir).children.select { |c| c.directory? }

task default: %w[ test ]

desc 'run all tests'
task :test do
  integration_test_dirs.each do |d|
    rakefile = d + 'Rakefile'
    if rakefile.exist? and rakefile.file?
      Dir.chdir(d) do
        puts "entering to %s" % [ d ]
        begin
          puts 'running rake'
          sh 'rake'
        ensure
          sh 'rake clean'
        end
      end
    else
      puts 'Rakefile does not exists, skipping'
    end
  end
end
