# Smallworld-short-transaction-broadcaster
a broadcaster for Smallworld GE short transaction server, for more information please see Visual Description part.

### visual description
![](https://github.com/Aramideh/Smallworld-short-transaction-broadcaster/blob/master/Module_Description.png)


### Getting Started

for the senario to work, you have to calibrate short transaction server and client.

##### Server
* load appserver.msf image
* smallworld_product.open_database(admin_dir)
* module_args<< {_unset, :save_magikc?, _true , :force_reload?, _true}
* sw_module_manager.load_module( "short_transaction_manager_server", _scatter module_args) 
* load short_transaction_server_listener module
* smallworld_product.start_server( a_ds_view_name , port) port in this method is the short transaction port
* short_transaction_server_listener.start()
##### Client
* start a short transaction for example v.start_short_transaction() 
* load short_transaction_client_listener module
* short_transaction_client_listener.start()

### Testing

in the client image call "call_dsst_server" procedure 
```
call_dsst_server ( "short_transaction_server_name" , {"COMMAND_1","hi"} , 3041 )
```


you should see something like this in the server cli
```
data...str..:COMMAND_1
data...str..:hi
data...str..:unset
getting clients...
no of clients:1
broadcasting...to 192.168.64.1	gis-server	sw:byte_vector:[1-4]	command:SERVER_COMMAND_1	data:hi back!
```


and immediatly in the clients cli you shoud see :
```
   doing something!......
```


