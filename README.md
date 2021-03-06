[![Known Vulnerabilities](https://snyk.io/test/github/ioanniswd/runlambda/badge.svg?targetFile=package.json)](https://snyk.io/test/github/ioanniswd/runlambda?targetFile=package.json)


## Instalation
```sh
~$ sudo npm install -g runlambda
```

## Requirements
[uplambda](https://github.com/ioanniswd/uplambda) CLI tool to upload code to an AWS Lambda Function and handle AWS API Gateway and permissions. Creates config .uplambda.json file used for usage with multiple AWS accounts.

## Arguments
| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [payload] | <code>json file</code> | none | Payload for lambda invocation |
| [name] | <code>attribute</code> | none | Which specific attribute from payload.json to use as payload |
| [published] | <code>boolean</code> | false | Whether to invoke the lambda alias (found in package json) instead of $LATEST |

## Usage

**Runs lambda function ($LATEST) with no payload:**
```bash
~/repos/lambda_function$ runlambda
```
**Runs lambda function with alias the lambdaAlias found in package json:**
```bash
~/repos/lambda_function$ runlambda --published
```

**Runs lambda function and shows the Response**
```bash
~/repos/lambda_function$ runlambda --verbose
```

**Runs lambda function and simulates prodv4_6 version**
```bash
~/repos/lambda_function$ runlambda --simver prodv4_6
```

**Runs lambda function with payload the json file:**
```sh
~/repos/lambda_function$ runlambda --payload payload.json
// payload.json:
// {
//   store_id: 'store_id',
//   group: 'group'
// }
```

**Runs lambda function with payload an object in json file:**
```sh
~/repos/lambda_function$ runlambda --payload payload.json --name payload2
// payload.json:
// {
//   payload1: {
//     store_id: 'store_id',
//     group: 'group'
//   },
//   payload2: {
//     store_id: 'store_id2',
//     group: 'group2'
//   }  
// }
```

**Example**
```sh
~/repos/createorder $ runlambda --payload payload.json --name demo_sample_order --published --simver prodv4_6 --verbose
```
