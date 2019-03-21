# Secretary - NodeJS Secrets Management 
[![Build Status](https://travis-ci.org/secretarysecrets/node.svg?branch=master)](https://travis-ci.org/secretarysecrets/node)
[![codecov](https://codecov.io/gh/secretarysecrets/node/branch/master/graph/badge.svg)](https://codecov.io/gh/secretarysecrets/node)

___

Secretary (etymology: Keeper of secrets) provides an abstract way to manage (currently only retrieve) secrets.

Currently supports the following adapters:

* [AWS Secrets Manager](https://github.com/secretarysecrets/node-aws-secrets-manager)
* [AWS Credstash](https://github.com/secretarysecrets/node-aws-credstash)
* [Hashicorp Vault](https://github.com/secretarysecrets/node-hashicorp-vault)
* [JSON File](https://github.com/secretarysecrets/node-json-file)

## Installation 

```bash
// If you want to use AWS Secrets Manager
$ npm install @secretary/core @secretary/aws-secrets-manager

// If you want to use Hashicorp Vault
$ npm install @secretary/core @secretary/node-vault

// If you want to use a JSON file
$ npm install @secretary/core @secretary/json-file
```

## Usage

```typescript
import Secretary from '@secretary/core';
import Adapter from '@secretary/aws-secrets-manager';
import {SecretsManager} from 'aws-sdk';

const manager = new Secretary({
    adapter: new Adapter({client: new SecretsManager()})
});

async function main() {
    const someSecret = await manager.getSecret('redis_host', 'some/secret/path');
    
    console.log(someSecret); // redis://localhost:6379
}
```
