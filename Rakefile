
desc "Install all external content"
task :install_modules do
  sh "librarian-puppet install \-\-path=puppet/modules"
end

desc "Update all external content"
task :update_modules do
  sh "librarian-puppet update"
end

desc  "destroy  db node "
task :destroy       => ['destroy:dbasm']

desc  "Create  db node "
task :db       => [:dbasm]

desc  "create dbasm vagrant node"
task :dbasm       => ['up:dbasm','halt:dbasm','storage:dbasm']


desc  "Up db node"
task :up        => ['up:dbasm']


desc  "Provision both nodes"
task :provision        => ['provision:dbasm']

VDI_FILES = (1..9).collect {|i| "ssdisk#{i}.vdi"}


rule /\.vdi$/ do |vdi|
  sh "vboxmanage createhd --filename #{vdi} --size 2048 --variant Fixed"
end


desc "VM up tasks"
namespace :up do

  desc "Create dbasm VM"
  task :dbasm => VDI_FILES do
    sh "vagrant up dbasm --provider=virtualbox --no-provision"
  end

end

desc "VM halt tasks"
namespace :halt do

  desc "Halt dbasm VM"
  task :dbasm do
    sh "vagrant halt dbasm --force"
  end

end

desc "Provision VM's"
namespace :provision do

  desc "provision dbasm VM"
  task :dbasm do
    sh "vagrant provision dbasm"
  end

end


desc "VM destroy tasks"
namespace :destroy do

  desc "destroy dbasm VM"
  task :dbasm do
    sh "vagrant destroy dbasm"
  end

end


desc "Storagetasks"
namespace :storage do

  desc "configure dbasm"
  task :dbasm do
    create_controller('dbasm')
    connect_disks('dbasm')
  end

end

def create_controller(vm)
  puts "Creating controller"
  sh "vboxmanage storagectl #{vm} --add sata --portcount 10 --name 'SATA Controller'"
end

def connect_disks(vm)
  controller_name = "SATA Controller"
  vdi_files = Dir.glob('*.vdi')
  vdi_files.each_with_index do |vdi_file, no|
    puts "Connect disk #{vdi_file}"
    sh "vboxmanage storageattach #{vm} --storagectl 'SATA Controller' --port #{no} --device 0 --type hdd --medium #{vdi_file} --mtype shareable"
  end
end

