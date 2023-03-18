Key password: 12345678
Secret phrase:       very museum phone decade snack design lock throw brother fly dwarf great
  Network ID:        substrate
  Secret seed:       0xbe9f179926a539cd0e27400f09b3f902826e30d9ef64e0675682c81a4344c616
  Public key (hex):  0x00fb3eb89b326db889521f202fd81e20ba85e755c03ce02b6649c1d1cf15aa6d
  Account ID:        0x00fb3eb89b326db889521f202fd81e20ba85e755c03ce02b6649c1d1cf15aa6d
  Public key (SS58): 5C5zVX5WH5PoHAPR27xus3CvvUVo6egT1VRs2NGZMYRe2o2s
  SS58 Address:      5C5zVX5WH5PoHAPR27xus3CvvUVo6egT1VRs2NGZMYRe2o2s

./target/release/node-template key inspect --password-interactive --scheme Ed25519 "very museum phone decade snack design lock throw brother fly dwarf great"
Key password: 12345678
Secret phrase:       very museum phone decade snack design lock throw brother fly dwarf great
  Network ID:        substrate
  Secret seed:       0xbe9f179926a539cd0e27400f09b3f902826e30d9ef64e0675682c81a4344c616
  Public key (hex):  0xf434ac5bff2bd59b76b11f3e408d9019c1fe8aaaced3224ff45fd2969f427c01
  Account ID:        0xf434ac5bff2bd59b76b11f3e408d9019c1fe8aaaced3224ff45fd2969f427c01
  Public key (SS58): 5HauBsZXjaRfBDmotWorrEh15W2mGB7c33H7o7mHdCfZGvDf
  SS58 Address:      5HauBsZXjaRfBDmotWorrEh15W2mGB7c33H7o7mHdCfZGvDf



Key 2: 
Key password: 12345678
Secret phrase:       tide front tattoo nerve kingdom resist organ recipe chicken chimney area then
  Network ID:        substrate
  Secret seed:       0x1d78c2e3243ba2a497dabf1febc9f8a3e60527b5f3857e438864fca4cd568727
  Public key (hex):  0x5c6bc578b45d3c3ff32b2abb7ec5f6e568526ac04a574e87fd795464fe17b104
  Account ID:        0x5c6bc578b45d3c3ff32b2abb7ec5f6e568526ac04a574e87fd795464fe17b104
  Public key (SS58): 5E9tH3DfTK4ocWWvM87N54c3wDzGdh496cRgFAenKvWzrHzz
  SS58 Address:      5E9tH3DfTK4ocWWvM87N54c3wDzGdh496cRgFAenKvWzrHzz

./target/release/node-template key inspect --password-interactive --scheme Ed25519 "tide front tattoo nerve kingdom resist organ recipe chicken chimney area then"
Key password: 12345678
Secret phrase:       tide front tattoo nerve kingdom resist organ recipe chicken chimney area then
  Network ID:        substrate
  Secret seed:       0x1d78c2e3243ba2a497dabf1febc9f8a3e60527b5f3857e438864fca4cd568727
  Public key (hex):  0xb5be7c5872c6e3f45d0f954a614ccc192e886ec6d6697704fb47a4ff18ec0165
  Account ID:        0xb5be7c5872c6e3f45d0f954a614ccc192e886ec6d6697704fb47a4ff18ec0165
  Public key (SS58): 5GB17MYVuVxtirTXerTR6QCvQaVBkes6cgQRUgJWywY4uVhP
  SS58 Address:      5GB17MYVuVxtirTXerTR6QCvQaVBkes6cgQRUgJWywY4uVhP


Node 1: 5HauBsZXjaRfBDmotWorrEh15W2mGB7c33H7o7mHdCfZGvDf
Node 2: 5GB17MYVuVxtirTXerTR6QCvQaVBkes6cgQRUgJWywY4uVhP

// 12D3KooWFHJBrGApB2h68hU3WCBF4QsBkznPMcpxSE3zaR3Wz2qe
./target/release/node-template \
  --base-path /tmp/node01 \
  --chain ./customSpec.json \
  --port 30333 \
  --ws-port 9945 \
  --rpc-port 9933 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode01 \
  --password-interactive


./target/release/node-template key insert --base-path /tmp/node01 \
  --chain customSpec.json \
  --scheme Sr25519 \
  --suri "very museum phone decade snack design lock throw brother fly dwarf great" \
  --password-interactive \
  --key-type aura

./target/release/node-template key insert \
  --base-path /tmp/node01 \
  --chain customSpec.json \
  --scheme Ed25519 \
  --suri "very museum phone decade snack design lock throw brother fly dwarf great" \
  --password-interactive \
  --key-type gran

// Spin Node 2: 12D3KooWRR5HysAkD7NL5gdj7MTUf8syfQRSajDLu5DVqBSj9Qw3
./target/release/node-template \
  --base-path /tmp/node02 \
  --chain ./customSpec.json \
  --port 30334 \
  --ws-port 9946 \
  --rpc-port 9934 \
  --telemetry-url "wss://telemetry.polkadot.io/submit/ 0" \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode02 \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWFHJBrGApB2h68hU3WCBF4QsBkznPMcpxSE3zaR3Wz2qe \
  --password-interactive


// second-participant-secret-seed
./target/release/node-template key insert --base-path /tmp/node02 \
  --chain customSpec.json \
  --scheme Sr25519 \
  --suri "tide front tattoo nerve kingdom resist organ recipe chicken chimney area then" \
  --password-interactive \
  --key-type aura

ls /tmp/node02/chains/local_testnet/keystore

// Shut down the node by pressing Control-c.

// 12D3KooWRR5HysAkD7NL5gdj7MTUf8syfQRSajDLu5DVqBSj9Qw3
./target/release/node-template \
  --base-path /tmp/node02 \
  --chain ./customSpec.json \
  --port 30334 \
  --ws-port 9946 \
  --rpc-port 9934 \
  --telemetry-url 'wss://telemetry.polkadot.io/submit/ 0' \
  --validator \
  --rpc-methods Unsafe \
  --name MyNode02 \
  --bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWFHJBrGApB2h68hU3WCBF4QsBkznPMcpxSE3zaR3Wz2qe \
  --password-interactive


// you should see the same genesis block and state root hashes.
// state root hash: 0xfa05e1497bc6ba354bd9ba979a997362cf6292b0f1006b8f7efa98f39a259231

### Pre funded accounts in dev/local chain
// Pre-funded accounts
```
				vec![
					get_account_id_from_seed::<sr25519::Public>("Alice"),
					get_account_id_from_seed::<sr25519::Public>("Bob"),
					get_account_id_from_seed::<sr25519::Public>("Charlie"),
					get_account_id_from_seed::<sr25519::Public>("Dave"),
					get_account_id_from_seed::<sr25519::Public>("Eve"),
					get_account_id_from_seed::<sr25519::Public>("Ferdie"),
					get_account_id_from_seed::<sr25519::Public>("Alice//stash"),
					get_account_id_from_seed::<sr25519::Public>("Bob//stash"),
					get_account_id_from_seed::<sr25519::Public>("Charlie//stash"),
					get_account_id_from_seed::<sr25519::Public>("Dave//stash"),
					get_account_id_from_seed::<sr25519::Public>("Eve//stash"),
					get_account_id_from_seed::<sr25519::Public>("Ferdie//stash"),
				],
```

### substrate account
tray over muffin monster decline labor dream math kidney find task turkey

### susbstrate permissioned network with node-authorization-pallate

Alice
Key type	Key value
Node key	c12b6d18942f5ee8528c8e2baf4e147b5c5c18710926ea492d09cbd9f6c9f82a
Peer identifier generated from the node key	12D3KooWBmAwcd4PJNJvfV89HwE48nwkRmAgo8Vy3uQEyNNHBox2
Peer identifier decoded to hex	0x0024080112201ce5f00ef6e89374afb625f1ae4c1546d31234e87e3c3f51a62b91dd6bfa57df

Bob
Key type	Key value
Node key	6ce3be907dbcabf20a9a5a60a712b4256a54196000a8ed4050d352bc113f8c58
Peer identifier generated from the node key	12D3KooWQYV9dGMFoRzNStwpXztXaBUjtPqi6aU76ZgUriHhKust
Peer identifier decoded to hex	0x002408011220dacde7714d8551f674b8bb4b54239383c76a2b286fa436e93b2b7eb226bf4de7

Charlie
Key type	Key value
Node key	3a9d5b35b9fb4c42aafadeca046f6bf56107bd2579687f069b42646684b94d9e
Peer identifier generated from the node key	12D3KooWJvyP3VJYymTqG7eH4PM5rN4T2agk5cdNCfNymAqwqcvZ
Peer identifier decoded to hex	0x002408011220876a7b4984f98006dc8d666e28b60de307309835d775e7755cc770328cdacf2e

Dave
Key type	Key value
Node key	a99331ff4f0e0a0434a6263da0a5823ea3afcfffe590c9f3014e6cf620f2b19a
Peer identifier generated from the node key	12D3KooWPHWFrfaJzxPnqnAYAoRUyAHHKqACmEycGTVmeVhQYuZN
Peer identifier decoded to hex	0x002408011220c81bc1d7057a1511eb9496f056f6f53cdfe0e14c8bd5ffca47c70a8d76c1326d

Spin Validator 1: // Local Node Identity: 12D3KooWBmAwcd4PJNJvfV89HwE48nwkRmAgo8Vy3uQEyNNHBox2 // 9944
./target/release/node-template \
--chain=local \
--base-path /tmp/validator1 \
--alice \
--node-key=c12b6d18942f5ee8528c8e2baf4e147b5c5c18710926ea492d09cbd9f6c9f82a \
--port 30333 \
--ws-port 9944

Spin Validator 2:  // Local Node Identity: 12D3KooWQYV9dGMFoRzNStwpXztXaBUjtPqi6aU76ZgUriHhKust //9945
./target/release/node-template \
--chain=local \
--base-path /tmp/validator2 \
--bob \
--node-key=6ce3be907dbcabf20a9a5a60a712b4256a54196000a8ed4050d352bc113f8c58 \
--bootnodes /ip4/127.0.0.1/tcp/30333/p2p/12D3KooWBmAwcd4PJNJvfV89HwE48nwkRmAgo8Vy3uQEyNNHBox2 \
--port 30334 \
--ws-port 9945

Add a third node to the list of well-known nodes // Local Node Identity: 12D3KooWJvyP3VJYymTqG7eH4PM5rN4T2agk5cdNCfNymAqwqcvZ //9946
./target/release/node-template \
--chain=local \
--base-path /tmp/validator3 \
--name charlie  \
--node-key=3a9d5b35b9fb4c42aafadeca046f6bf56107bd2579687f069b42646684b94d9e \
--port 30335 \
--ws-port=9946 \
--offchain-worker always

Authorize access for the third node

Allow connections from a sub-node

Claim the sub-node

Start the sub-node

Allow connections to the sub-node