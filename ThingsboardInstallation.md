## Setup for Creating/ Activating Thingboard CE (on Ubuntu/Linux/ Ubuntu WSL for Windows)

•	Prepare environment:
>	Set-up Ubuntu 1804/2004 Linux desktop environment
>	WSL2 for Linux
>	Dual boot with Window
>	VirtualBox
•	Install Postgres
		Step 1. sudo apt update
		Step 2. sudo apt install postgresql postgresql-contrib 
			            or,
		                 sudo apt install postgresql 
•	Install JDK
	Steps: 
		Step 1  	sudo apt update
		Step 2  	sudo apt install openjdk-8-jdk
		Step 3  	java -version

•		Install SDKMAN
		Step 1 	 curl -s "https://get.sdkman.io" | bash

		Step 2          source "$HOME/.sdkman/bin/sdkman-init.sh"
•	Install maven
			sdk install maven

Now for SETUP Application: 
	

##Setting up GitHub: 
Step 1.  ->
 https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
Step 2. ->
https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account

After completing the above steps try the following steps: 
# Get code

# upload SSH key to Github account and clone the app
•	git clone git@github.com:Nibiaa-Devices-IoT-platforn/thingsboard.git

# if not and don't want to, use HTTPS
•	git clone https://github.com/Nibiaa-Devices-IoT-platforn/thingsboard.git


# Install dependencies
•	cd thingsboard
•	mvn clean install -DskipTests


#Now, Start the Postgres Server

•	sudo service postgres start

# Set-up DB
•	psql -U postgres -d postgres -h 127.0.0.1 -W
•	CREATE DATABASE thingsboard;
•	\q


>> if you encounter password validation error,

	sudo -u postgres psql -c "ALTER USER postgres PASSWORD 'postgres';"



# Seed DB

•	cd application/target/bin/install
•	sudo chmod 755 install_dev_db.sh
•	sudo ./install_dev_db.sh

Now, just go back to the thingsboard folder by << cd .. >>

# Run server (from the root directory of the app) on http://localhost:8080

•	java -jar application/target/thingsboard-3.2.0-SNAPSHOT-boot.jar


After this Process just open the following link on your Web Browser:

•	http://localhost:8080



Alternatively (Optional Step *Not Required.. )

# And, optionally run server with hot UI reloading on http://localhost:4200

•	cd ui-ngx
•	mvn clean install
•	yarn start


For more details… (Do check these)
https://github.com/Nibiaa-Devices-IoT-platforn/thingsboard/wiki/Setup
https://github.com/Nibiaa-Devices-IoT-platforn/thingsboard/wiki/To-read#git-and-github

