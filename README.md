7 nodes example
	1) ./init.sh will configure nodes. init.sh: Initialize accounts and keystores
		-- voter nodes
			[*] Configuring node 2 as block maker and voter
			[*] Configuring node 4 as voter
			[*] Configuring node 5 as voter
		
		-- block maker nodes
			[*] Configuring node 2 as block maker and voter
			
		-- underpriveleged nodes
			[*] Configuring node 1
			[*] Configuring node 3
			[*] Configuring node 6
			[*] Configuring node 7
	
	*This is as defined in the file "genesis.json".
	
	*the variables VoteAccount, voteaccountpassword are defined in file : https://github.com/jpmorganchase/quorum/blob/b6286320efc4189419a8e0f7f28f9af50f71b3ff/cmd/utils/flags.go

	*to make a node a voter we can define it as :
		PRIVATE_CONFIG=tm4.conf nohup geth --datadir qdata/dd4 $GLOBAL_ARGS --rpcport 22003 --port 21003 --voteaccount "0x9186eb3d20cbd1f5f992a950d808c4495153abd5" --votepassword "" 2>>qdata/logs/4.log &

	*to make a node block maker and voter we can define it as:
		PRIVATE_CONFIG=tm2.conf nohup geth --datadir qdata/dd2 $GLOBAL_ARGS --rpcport 22001 --port 21001 --voteaccount "0x0fbdc686b912d7722dc86510934589e0aaf3b55a" --votepassword "" --blockmakeraccount "0xca843569e3427144cead5e4d5999a3d0ccf92b8e" --blockmakerpassword "" --singleblockmaker --minblocktime 2 --maxblocktime 5 2>>qdata/logs/2.log &

	*transfer from node 1 to node 7 is written in the contract file : https://github.com/jpmorganchase/quorum-examples/blob/master/examples/7nodes/script1.js

	*
