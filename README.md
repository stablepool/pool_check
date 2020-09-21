# pool_check
Security script to check your Cardano Node for vulnerabilities and to monitor key-settings to notify the pool operator in case anything is modified against their will. The information is stored in a compact file, containing the key configuration of your node.

Get the pool_check by pulling from github. Navigate to the folder containing pool_check and run it from the command line by:

pool_check

The script will run and generate a file called pool.security containing all the security info on your cardano pool - like needed updates, ssh port/password/login configurations, connected IP's and open ports. If severe warnings are detected the script will notify you in the console, if not - please inspect pool.security carefully for any configurations which might be insecure.

pool_check comes with no warrenty and you are running it at your own risk.

Happy staking and happy operation to your stake-pools out there!
