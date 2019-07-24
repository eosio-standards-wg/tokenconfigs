tokenconfigs: token contract identification table
=================================================


EOSIO Standards Working Group, 2019

https://github.com/eosio-standards-wg


Introduction
------------

Multiple independent teams are developing their token contracts, and
quite often it's challenging for a block explorer or for a wallet to
identify a token and retrieve its balance (or other attributes for
nonfungible tokens).


This standard proposal introduces a uniform way for token contracts to
declare themselves and to help user applications retrieve and manipulate
the token iinformation.


Table definition
----------------

```
  TABLE tokenconfigs {
    name           standard;
    std::string    version;
  };

  typedef singleton<"tokenconfigs"_n, tokenconfigs> s_tokenconfigs;
```


The table MUST be initialized before any tokens and balances are created
by the contract.

The table MUST have only one row (singleton class is most suitable for
this).

The table MUST be declared in contract ABI as "tokenconfigs".

The `standard` field MUST contain a name from the list in the next
section. If your project is not listed, open a pull request or an issue
in tokenconfigs repository.

The `version` string MUST contain only digits and dots, following
"MAJOR.MINOR.PATCH" pattern as described in Semantic Versioning
(https://semver.org/). PATCH version is optional and can be omitted.

Smart contracts MAY add more fields to the structure **after** the
`version` field, but their semantics are not standardized.


Known standard names
--------------------

* `simpleassets`, Simple Assets by Cryptolions
  (https://github.com/CryptoLions/SimpleAssets)

* `dgoods`, dGoods by Mythical Games (https://dgoods.org/)

* `dsp`, tokens based on Zeus dApp Software development Kit by
  LiquidApps (https://liquidapps.io/)

* `dnft`, Distributed Ownership NFT by Quillhash
  (https://github.com/Quillhash/dnfts)




Copyright and License
---------------------

Copyright 2019 EOSIO Standards Working Group

This work is licensed under a Creative Commons Attribution 4.0
International License.

http://creativecommons.org/licenses/by/4.0/


