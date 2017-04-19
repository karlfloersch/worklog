## April 18th

* [x] Set focus
* [x] Update local Pyethereum to reflect yesterday's changes
* [x] Create Consensus Protocols working group
* [x] Ujo call
* [ ] ~~Revamp the stupid `casper_utils.py` because let's be real, it sucks~~

* Alternate approach
  * Instead of using the casper utils, I am going to instead try to isolate the functionality which needs to be added to `chain.py` and the miner and just use the Ethereum tester
  * This will be faster and should solve my horrible bug
  * \[PROBLEM\] - The tester doesn't mine blocks or have a concept of a chain. I feel like fixing the bug might be less work than figuring out how to use the tester with the miner and chain :\(

* [x] Help debug a wallet issue
* [x] Create `inject_casper_constracts` which primes the state for Casper
* [x] Rebuild the entire `casper_utils` and testing file in order to fix the bug.... -- result: got the exact same result
* [x] Replace `set_code()` with a normal create contract transaction \(should have done this long ago\)
* [x] Fix out of gas error
* [x] **Finally fix the bug!!!!!! **

## April 17th

* [x] Ujo call
* [x] Casper standup call
* [x] Go to Consensys office
* [x] Fix Python3 support for `chain.py` PR by removing the dependency on future [https://github.com/ethereum/pyethereum/pull/710](https://github.com/ethereum/pyethereum/pull/710)
* [x] Fix a bunch of Ujo bugs
* [x] Meet Meher Roy and begin discussing super cool & top secret plans :\) 

## April 16th

* [x] Initialize the new `casper` repository
* [x] Determine repository structure

* Created two directories, `contracts` and `daemon` which can be imported and used either as libraries or as a cli

* [x] Merge V's commits

* [x] Push! \( github.com/ethereum/casper \)

## April 15th

* [x] Tests `apply_msg` in Python2.7 -- result: it still has the issue

## April 14th

* [x] Submit Python3 `chain.y` compatibility PR \([https://github.com/ethereum/pyethereum/pull/710\](https://github.com/ethereum/pyethereum/pull/710%29\)
* [x] Begin VM tests with Python2 & Python3

## April 13th

* [x] Fix the `ethereum1_check_header` error

* It turns out the issue was I wasn't mining the block

* [x] Add Ujo tasks to PT

* [x] Ujo call

* [x] Mine the block before continuing the chain -- result: the mining worked; however, when trying to add transactions it didn't :'\(

* [x] Helped Gael with his bug
* [x] Get mining empty blocks working
* [x] Fix broken tests in `test_chain.py`

* Pushed up a new branch which has the changes: [https://github.com/karlfloersch/pyethereum/tree/state\_revamp\_python3\_chain\_tests](https://github.com/karlfloersch/pyethereum/tree/state_revamp_python3_chain_tests)

## April 12th

* [x] Compare the state before and after applying a transaction which alters the state--result: no change was made
* [x] Compare the state before & after running `casper_contract_bootstrap()` -- result: seems to have actually changed the state! This is super exciting! :D
* [x] Try using testing instead of `initiate()` for the bootstrap -- result: testing also changes the state!
* [x] Try committing without calling anything \(maybe that is what's really happening\) -- result: turns out the only changes to the state were from the commit, which suggests it's from the call to `initialize()` which sets the Casper code. The transactions are still not working
* [x] Test creating blocks and applying the transactions
* [x] Ujo Call
* [x] Architecture call
* [x] Create second block to build on the chain -- result: this caused an error with `ethereum1_check_header` failing

## April 11th

* [x] Look into V's alternate scheme for verifying that prepares are sent while the validator is logged in
* [x] Test to see if `call_casper` works in the old repo

* It works and returns exactly what I'm looking for

* [x] ~~Try the old ~~~~`call_casper` in Python3 and see if it works~~ -- This is taking way too long, and doesn't seem to be worth the effort

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



