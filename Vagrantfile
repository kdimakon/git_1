Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
    config.vm.provider "virtualbox" do |vb|
       vb.gui = false
       vb.memory = "1024"
    end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update && apt upgrade -y
    # Create a folder
    runuser -l vagrant -c 'mkdir actions-runner && cd actions-runner'
    # Download the latest runner package
    runuser -l vagrant -c 'curl -o actions-runner-linux-x64-2.285.1.tar.gz -L https://github.com/actions/runner/releases/download/v2.285.1/actions-runner-linux-x64-2.285.1.tar.gz'
    # Extract the installer
    runuser -l vagrant -c 'tar xzf ./actions-runner-linux-x64-2.285.1.tar.gz'
    # Create the runner and start the configuration experience
    runuser -l vagrant -c './config.sh --url https://github.com/kdimakon/git_1 --token AW2NUHWF3HS7JZBEHLGG7ELBWICBA'
    # Last step, run it!
    runuser -l vagrant -c './run.sh'
  SHELL
end

