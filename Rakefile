require 'erb'
require 'json'

task :default => :build

task :build do
  sentences = File.readlines('sentences.txt').map do |line|
    match = /\A(\d+)\.\s+(.*)\z/.match(line.chomp)
    { id: match[1].to_i, text: match[2] }
  end

  content = ERB.new(File.read('set-lyrics.js.erb')).result(binding)

  open('set-lyrics.js', 'w') {|io| io << content }
end