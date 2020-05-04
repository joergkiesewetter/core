# Fork
This fork aims to give an out-of-the-box running docker container to just let you run a terrad node.

Last tested with terra-core v0.3.5.

# Instructions

* download genesis file from here: https://github.com/terra-project/launch/tree/master/columbus-3
* unfortunately, there is a bug in the file. You need to change the field `app_state.gentxs` to make it work:
  * from ```"gentxs": Null, ```
  * to ```"gentxs": [] ```
* navigate into the folder and execute:
  * docker-compose -f docker-compose.yml up --build
* when the container is running, open a new command line window and open a new shell in it with:
  *  ```docker exec -ti <container_id> bash```
* execute the following command in the shell to start the rest-server
  * ```terracli rest-server --chain-id=columbus-3 --node tcp://localhost:26657 --trust-node=false --laddr=tcp://0.0.0.0:1317```
* now, you can query the rest-server from the host with queries like: 
  * ```http://localhost:1317/txs?tx.height=8727&limit=100&page=1```
