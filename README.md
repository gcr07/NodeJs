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


# Java script 

## Funciones asincronas asyc await

Para definir una funcion asincrona se usa "async" antes de la funcion por ejmeplo:

```
async function getOracleContract (web3js) {
    const networkId = await web3js.eth.net.getId();
    return new web3js.eth.Contract(OracleJSON.abi, OracleJSON.networks[networkId].address) //instance del contrato
}


```

## Diferencia entre var,let y const

Las declaraciones ***var*** tienen un ámbito global o un ámbito función/local, mientras que ***let y const*** tienen un ámbito de bloque.

### VAR 

El ámbito es global cuando una variable var se declara fuera de una función. Esto significa que cualquier variable que se declare con var fuera de una función está disponible para su uso en toda la pantalla.

var tiene un ámbito local cuando se declara dentro de una función. Esto significa que está disponible y solo se puede acceder a ella dentro de esa función.

Ejemplo:

```
    var tester = "hey, hola";
    
    function nuevaFuncion() {
        var hola = "hola";
    }
    console.log(hola); // error: hola is not defined
```

### Problema con var

```
    var saludar = "hey, hola";
    var tiempos = 4;

    if (tiempos > 3) {
        var saludar = "dice Hola tambien"; 
    }
    
    console.log(saludar) // "dice Hola tambien"
```
>Por lo tanto, como tiempos > 3 devuelve true, saludar se redefine para "dice Hola tambien". Aunque esto no es un problema si quieres redefinir saludar a conciencia, se convierte en un problema cuando no te das cuenta de que la variable saludar ha sido definida antes.
Si has utilizado saludar en otras partes de tu código, puede que te sorprenda la salida que puedes obtener. Esto probablemente causará muchos errores en tu código. Por eso son necesarios let y const

## LET

let es ahora preferible para la declaración de variables. No es una sorpresa, ya que es una mejora de las declaraciones con var. También resuelve el problema con var que acabamos de cubrir. Consideremos por qué esto es así.

let tiene un ámbito de bloque
Un bloque es un trozo de código delimitado por {}. Un bloque vive entre llaves. Todo lo que está dentro de llaves es un bloque.

Así que una variable declarada en un bloque con let  solo está disponible para su uso dentro de ese bloque. Permíteme explicar esto con un ejemplo:


```
let saludar = "dice Hola";
   let tiempos = 4;

   if (tiempos > 3) {
        let hola = "dice Hola tambien";
        console.log(hola);// "dice Hola tambien"
    }
   console.log(hola) // hola is not defined

``` 

let puede modificarse pero no volver a declararse.
Al igual que var,  una variable declarada con let puede ser actualizada dentro de su ámbito. A diferencia de var, una variable let no puede ser re-declarada dentro de su ámbito. Así que mientras esto funciona:

```
   let saludar = "dice Hola";
    saludar = "dice Hola tambien";
```

***esto devolverá un error:***

```  
 let saludar = "dice Hola";
 let saludar = "dice Hola tambien"; // error: Identifier 'saludar' has already been declared
```

***Sin embargo si  se define en diferentes ambitos***

```
    let saludar = "dice Hola";
    if (true) {
        let saludar = "dice Hola tambien";
        console.log(saludar); // "dice Hola tambien"
    }
    console.log(saludar); // "dice Hola
```

## Hoisting de let

Al igual que  var, las declaraciones let se elevan a la parte superior. A diferencia de var que se inicializa como undefined, la palabra clave let no se inicializa. Sí que si intentas usar una variable let antes de declararla, obtendrás un Reference Error.

## Const

Las variables declaradas con const mantienen valores constantes. Las declaraciones const similitudes con las declaraciones let.

Las declaraciones const tienen un ámbito de bloque
Al igual que las declaraciones let, solamente se puede acceder a las declaraciones const dentro del bloque en el que fueron declaradas.

const no puede modificarse ni volver a declararse
Esto significa que el valor de una variable declarada con const s el mismo dentro de su ámbito. No se puede actualizar ni volver a declarar. Así que si declaramos una variable con const, no podemos hacer esto:

>https://www.freecodecamp.org/espanol/news/var-let-y-const-cual-es-la-diferencia/#:~:text=Las%20variables%20var%20pueden%20ser,parte%20superior%20de%20su%20%C3%A1mbito.
