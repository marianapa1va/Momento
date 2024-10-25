# Momento

 Quantos funcionarios da empresa Momento trabalham no departamento de vendas?

 R: Na empresa Momento, há 10 funcionários. Sendo oito deles na área de consultoria de vendas, um deles com vendas e o ultimo como representante de vendas para a América Latina.

 ```js

db.funcionarios.countDocuments({departamento: ObjectId('85992103f9b3e0b3b3c1fe71')})

```
 Inclua suas próprias informações no departamento de Tecnologia da empresa.
 
  ```js
db.funcionarios.insertOne({
    "nome" : "Mariana Paiva" , 
    "telefone" : "123.123.1234" , 
    "email" : "M.mariana@gmail.com" ,
    "dataAdmissao" : "2025 - 02 - 07" ,
    "cargo" : "Mobile Developer" , 
    "salario" : "15000" ,
    "departamento" : "ObjectId('85992103f9b3e0b3b3c1fe74')"
})
```

 Agora diga, quantos funcionários temos ao total na empresa?

 R: 24 funciinários.
 
  ```js

db.funcionarios.countDocuments()

```

 E quanto ao Departamento de Tecnologia?

 R: Seis funcionários.
 
   ```js
db.funcionarios.countDocuments({departamento:ObjectId('85992103f9b3e0b3b3c1fe74')})

```
 Qual a média salarial do departamento de tecnologia?

 R: 18.900
 
  ```js
db.funcionarios.aggregate([
  { $match: { departamento: ObjectId('85992103f9b3e0b3b3c1fe74') } },
  { $group: { _id: null, mediaSalario: { $avg: "$salario" } } }
]);
```

 Quanto o departamento de Vendas gasta em salários? 

 R: O departamento de vendas gasta em torno de 300680 com salários mensais.
 
  ```js

db.funcionarios.aggregate([
  { $group: {
      _id: null, 
      mediaSalarial: { $avg: { $toDouble: "$salario" } } } }]);

```
 
 Um novo departamento foi criado. O departamento de Inovações. Ele será locado no Brasil. 
 Por favor, adicione-o no banco de dados da empresa colocando quaisquer informações que você achar relevantes.

//Função usada nas criações de "ObjectId".
   ```js
ObjectId()

```

 //função usada para criar o novo departamento de "inovações" da empresa.
 ```js
db.departamentos.insertOne({
    "_id": ObjectId("671bdbeadacc08f658f7c527"),
    "nome": "Inovações",
    "escritorio": ObjectId("671bde65dacc08f658f7c528")
});

```

//Função usada na criação do escritório para poder alocar o departamento de inovações.
  ```js
db.escritorios.insertOne({
  _id: ObjectId("671bde65dacc08f658f7c528"),
  nome: "Gabs Inovation",
  endereco: "Gabs Inovation, Lapa, São Paulo",
  telefone: "+55 251-755-0123",
  pais: "Brasil",
  suprimentos: [
    {
      produto: "Ominitrix",
      quantidade: 5,
      precoUnitario: 10000000
    },
    {
      produto: "Chapeu Seletor",
      quantidade: 10,
      precoUnitario: 510000
    },
    {
      produto: "Tapete Voador",
      quantidade: 10,
      precoUnitario: 2000000
    }
  ]
});

```

 O departamento de Inovações está sem funcionários. Inclua alguns colegas de turma nesse departamento.  
 
  ```js

db.funcionarios.insertMany([
    {
        "nome": "Iury Sven",
        "telefone": "11.9315.85697",
        "email": "iuryiury@gmail.com",
        "dataAdmissao": "2024-09-30",
        "cargo": "Mobile Developer",
        "salario": 15000,
        "departamento": ObjectId("671bdbeadacc08f658f7c527") 
    },
    {
        "nome": "Danilo Alcantra",
        "telefone": "11.93569.8897",
        "email": "dandan@gmail.com",
        "dataAdmissao": "2025-09-30",
        "cargo": "Mobile Developer",
        "salario": 15000,
        "departamento": ObjectId("671bdbeadacc08f658f7c527") 
    }
]);

```
 Quantos funcionarios a empresa Momento tem agora?

 R: 26 funcionários 
 
  ```js
db.funcionarios.countDocuments()

```

 Quantos funcionários da empresa Momento possuem conjuges?

 R: Sete pessoas possuem conjugues.
 
  ```js
db.funcionarios.countDocuments({ "dependentes.conjuge": { $exists: true }})

```

 Qual a média salarial dos funcionários da empresa Momento, excluindo-se o CEO?
 
  ```js

db.funcionarios.aggregate([
    {
        $match: {
            cargo: { $ne: "CEO" } 
        }
    },
    {
        $group: {
            _id: null, 
            mediaSalarial: { $avg: "$salario" }
        }
    }
]);

```

 Qual a média salarial do departamento de tecnologia? 
 
  ```js

```
 Qual o departamento com a maior média salarial?
  ```js
```
 Qual o departamento com o menor número de funcionários?
  ```js
```
 
 Pensando na relação quantidade e valor unitario, qual o produto mais valioso da empresa?
   ```js
```
 
 Qual o produto mais vendido da empresa?
   ```js
```
 
 Qual o produto menos vendido da empresa?
   ```js
```
