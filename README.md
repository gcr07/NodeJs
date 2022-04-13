# NodeJs

### Crear un proyecto

`npm init -y`

### Instalar dependencia

`npm i nombre`

### Buscar paquete

`npm search web3`

### Dependencias

`npm install -D	o --save-dev	Instala el paquete en el proyecto, como dependencia de desarrollo.`

`npm install --save-prod	Instala el paquete en el proyecto, como dependencia de producción.`

`npm install -g	o --global	Instala el paquete en el sistema, sin asociarlo al proyecto`

## Web3
```
npm install web3
```

## Install solidity compiler 
```
npm install solc
```


### Conexion Basica

```bash
const Web3 = require('web3')
const urlRpc = 'https://speedy-nodes-nyc.moralis.io/dd3f4019d376fef46ca1f578/eth/ropsten'; 
const web3 = new Web3(urlRpc)
console.log(web3)
```
### Obtener numero de transacciones de esa address

```bash
web3.eth.getTransactionCount('0x8A6c9cEa0f04f7e8D8f345d2Ec57e7eED465F678').then(res => {
      console.log(res)
    })
```
### Obtener balance

```bash
web3.eth.getBalance("0x8A6c9cEa0f04f7e8D8f345d2Ec57e7eED465F678", function(err, result) {
  if (err) {
    console.log(err)
  } else {
    console.log(web3.utils.fromWei(result, "ether") + " ETH")
  }
})
```

### Precio del gas

```bash
web3.eth.getGasPrice(function(err,res){console.log(res*21000)})
```

## Ethereum transacciones con Web3

```
const Web3 = require('web3')
const urlRpc = 'nodemolaris'; 

const web3 = new Web3(urlRpc)

addressFrom = '0x8A6c9c57e7eED465F678'
addressTo = '0x12FcCbf37a17895B83AA011'

const privKey = '952315'



//Create transaction

const deploy = async () => {
   console.log(`Attempting to make transaction from ${addressFrom} to ${addressTo}`);

   const createTransaction = await web3.eth.accounts.signTransaction(
      {
         from: addressFrom,
         to: addressTo,
         value: web3.utils.toWei('1', 'ether'),
         gas: '21000',
      },privKey);

console.log("imprimiendo createTransaction")
console.log(createTransaction)

// Deploy transaction
   const createReceipt = await web3.eth.sendSignedTransaction(createTransaction.rawTransaction);
   console.log(`Transaction successful with hash: ${createReceipt.transactionHash}`);
}; // Cierre de la llave principal

deploy();

//console.log(web3.utils.toWei('1', 'ether'))// convierte 1 ether a wei
```

## Crear una wallet desde codigo 

```
const Web3API = require('web3');

const main = () => {

const web3 = new Web3API(new Web3API.providers.HttpProvider('usemolaris'));
let account = web3.eth.accounts.create(web3.utils.randomHex(32));
let wallet = web3.eth.accounts.wallet.add(account);
let keystore = wallet.encrypt(web3.utils.randomHex(32));
console.log({ account: account,wallet: wallet,keystore: keystore});



};


main();


```




# Paginas que reolvieron errores 

Resolvio un error de importaciones
>https://exerror.com/uncaught-syntaxerror-cannot-use-import-statement-outside-a-module-when-importing-ecmascript-6/

# Paginas con ejemplos y cosas interesates 

Cabe destacar que este repositorio y todos son una recopilacion de interner de lo que voy estudiando se podria decir mis notas
>https://github.com/grinsteindavid/web3-javascript-etherium-examples


# Java script funciones asincronas asyc await

Para definir una funcion asincrona se usa "async" antes de la funcion por ejmeplo:

```
async function getOracleContract (web3js) {
    const networkId = await web3js.eth.net.getId();
    return new web3js.eth.Contract(OracleJSON.abi, OracleJSON.networks[networkId].address) //instance del contrato
}


```

