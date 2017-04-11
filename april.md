## April 11th

* [x] Look into V's alternate scheme for verifying that prepares are sent while the validator is logged in
* [x] Test to see if `call_casper` works in the old repo

* It works and returns exactly what I'm looking for

* [x] ~~Try the old `call_casper` in Python3 and see if it works~~ -- This is taking way too long, and doesn't seem to be worth the effort
* [x] Ujo call

* After trying a bunch of stuff, it seems that I might have to finalize the block before I can make the transactions that I need.

* [x] Figure out the relationship between `State` and `Chain` 

* State
  * Manages the Ethereum Merkle-Paricia-Trie 
  * Provides the ability to get & set values
    * `nonce`, `code`, `bytes`
  * Implements a cache which is used for storage & getting until you call `commit` to commit it to the DB
* Chain
  * Maintains a state object
  * Scores the block header hashes
    * Stores transactions by hash
    * Stores the transaction scores with `score:[block.header.hash] -> score`
  * Shares the `db` with it's state object
    * Snapshots can be reconstructed with this db given a specific `state_root` \(`merkle root`\)

* [ ] Try finishing the block and then making the call OR try debugging the `Not enough data for head` error

## April 10th

* [x] Determine focus for the day \[Focus: Add basic fork scoring rules\]
* [x] Submit fix for mediaplayer bug
* [x] Document Redux Persist
* [x] Begin talks around starting a consensus protocol working group for the EEA
* [x] Submit a PR which removes accidentally committed code in the ujo repo
* [x] Ujo & weekly Casper calls
* [x] Verify that the Casper contract is deployed when using `call_casper()`

* Notes on my findings

  * `apply_transaction` uses `apply_message`, and a major difference between the two seems to be that `apply-message` doesn't reduce the balance of the sender

* Potential areas to explore

  * Try running the Casper contract 

* [ ] Get the epoch\_length from the Casper contract, to be used to determine the current epoch from the validator's perspective

* [ ] Call `initialize_epoch()` at the start of every new epoch

## April 9th

* [x] Find print statement which was constantly flooding the console with `None 1`
* [x] Fix bugs when running the new `make_casper_genesis()`
* [x] Test getting some basic Casper contract messages to go through as expected
* [x] Fix bug which prevents transactions from going through
* [ ] Figure out what needs to be done about the blockheaders

* Ended up asking V what should be done

  * This also relates to how exactly the inflation will be handled. Each epoch there is a reward paid to active validators \(assuming they participate\). This ETH can be added to the contract in proportion to how much is generated, or the contract can be filled in large intervals. I haven't heard back from V yet but I'm curious what he thinks about this

* [ ] Start tracking the `chain.py` changes / head

* [ ] Add a class which is parallel to the Miner class which determines if, with the current state, it should send a commit/prepare tx

## April 8th

* [x] Get Gitbook setup for the brand new worklog!



