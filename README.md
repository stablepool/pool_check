# pool_check
Security script to check your Cardano Node for vulnerabilities and to monitor key-settings to notify the pool operator in case anything is modified against their will. The information is stored in a compact file, containing the key configuration of your node.

Get the pool_check by pulling from github. Navigate to the folder containing pool_check and run it from the command line by:

pool_check

The script will run and generate a file called pool.security containing all the security info on your cardano pool - like needed updates, ssh port/password/login configurations, connected IP's and open ports. If severe warnings are detected the script will notify you in the console, if not - please inspect pool.security carefully for any configurations which might be insecure.

HOW TO GET THE SCRIPT:
1. Go into your home directory
2. Fetch the script by git clone https://github.com/stablepool/pool_check
3. This will generate a pool_check subfolder in your home which you can cd into and proceed with the setup

HOW TO SETUP THE SCRIPT:
1. Adjust your email and folderpath in the pool_check script to a folder where you want to store the pool.security output. Choose a path located in your home like /home/user/pool_check. enter all the fields you want checked in "define_checks". A list of inputs is given below.
2. Move pool_check to /usr/bin so it can not be modified by non-root users. use "sudo mv pool_check /usr/bin"
3. Run pool_check once and check if an output file was generated at your specified folderpath. Check the output file if your configuration is as expected.
4. Store the hash of the file at a location not accessible by users. Use the provided script "sudo generate_checksum_and_store_it" to copy your checksum to /etc/pool_check.checksum
5. Cron pool_check to run at an interval. Do this by running:
crontab -e

#Now cron the script to run every hour by adding the following line:
0 */1 * * * /usr/bin/pool_check

#Check if your job was cron'ed 
crontab -l
6. Enjoy your pool_check script :) 

The script comes with features which can be controlled by the input file "define_checks". Valid entries are:

send_mail
check_for_changes
check_load_average 

where:
send_mail defines that the pool_check script will send you an email if your configuration changes. Be sure to adjust the email address in the pool_check file to your email and the folderpath the the folder where you want your pool.security to be generated. 

check_for_changes will check the checksum of your pool.security against one previously generated. be sure to run generate_checksum_and_store_it previously

check_load_average will check is the load average of your server is bigger than ncpus-1 - which means your server has a high load. pool_check will notify you by email if this happens.

An easy setup reads:
filepath="/home/user/pool_check"
email="your_email@provider.com"

define_checks:
send_mail
check_for_changes
check_load_average

pool_check comes with no warrenty and you are running it at your own risk.

Happy staking and happy operation to your stake-pools out there!
