# teamcity
1. Navigate into the directoy for your OS.
2. execute "docker-compose up --no-start"
3. execute "docker-compose start"
4. goto http://localhost:8111 in your browser and follow setup instructions (This config uses HSQL2) If you wish you can look at Teamcity examples for other database configs
5. Once server is running, Goto Administration -> Global Settings and set the Maximum build artifact file size: to -1 () You will need this for the db.tar files)
6. Goto Administration -> Projects Import andimport the supplied teamcity project
7. Select Agents from the top menu and Authorise the Cardano Build Agent

(Optional - This will update the db instead of starting form scratch)
8. Obtain a snapshot of your cardano db in tar.gz format and copy it to the agents/cardano-agent/archives directory and rename it to mainnet-db.tag.gz or testnet-db.tar.gz
9. Select projects -> Cardano Node -> Build Chains -> Run -> Changes -> Select the tag you wish to build and Run Build
10. Grab your artifatcs and upload them to your server
11. Leave this docker build running and it will build any new tags (1.2*) automatically 
12. Check the build time for the database update and decide if it is worth copying it or simply letting the node updat eby itself.
