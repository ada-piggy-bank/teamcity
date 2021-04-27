# Cardano Binaries teamcity build
1. Navigate into the directoy for your OS.
2. execute "docker-compose up --no-start"
3. execute "docker-compose start"
4. goto http://localhost:8111 in your browser and follow setup instructions (This config uses HSQL2) If you wish you can look at Teamcity examples for other database configs
5. Once server is running, Goto Administration -> Global Settings and set the Maximum build artifact file size: to -1 (You will need this for the db.tar.gz files)
6. Goto Administration -> Projects Import, and import the supplied teamcity project (TeamCity_CardanoNode.zip)
7. Select Agents from the top menu and Authorise the Cardano Build Agent
9. (Optional) Obtain a snapshot of your cardano db in tar.gz format and copy it to the agents/cardano-agent/archives directory and rename it to mainnet-db.tag.gz or testnet-db.tar.gz (This will really save a lot of time on your first build, especially mainnet) 
10. Select projects -> Cardano Node -> Build Chains -> Run -> Changes -> Select the tag you wish to build and Run Build
11. Grab your artifatcs and upload them to your server
12. Leave this docker build running and it will build any new tags (1.2*) automatically 
13. Check the build time for the database update and decide if it is worth copying it or simply letting the node update by itself.

Finally, if you are using windows, you might see all of your memory being consumed by vmmem process. This is WSL2.
You can limit the memory that this guy can have by following this guide.
https://medium.com/@lewwybogus/how-to-stop-wsl2-from-hogging-all-your-ram-with-docker-d7846b9c5b37

<h3>Tip</h3>The longer the gap between the release, the longer the database will take to update.
Check the relelase notes for the release to decide if the snapshot is needed for your nodes.
