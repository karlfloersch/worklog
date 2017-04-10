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



