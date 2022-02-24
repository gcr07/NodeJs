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


# Paginas que reolvieron errores

Resolvio un error de importaciones
>https://exerror.com/uncaught-syntaxerror-cannot-use-import-statement-outside-a-module-when-importing-ecmascript-6/





