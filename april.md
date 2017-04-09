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



