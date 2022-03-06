# Banco de Dados Mongo

## Configuração de Ambiente:

- **Instalar o Banco de Dados MongoDB** e **Mongodb Database Tools**:https://www.mongodb.com/

- **Instalar o CMDER**:  https://cmder.net/ _(para usar comandos linux)_

! Configurar nas Variaveis de Ambiente !

***

## Conceito:

O mongo é um banco de dados não relacional.

No banco para se referir a uma tabela, ou item do banco me refiro ao banco como um todo, então inicio com _db._

No Mongo usamos métodos para realizar ações

Comparando com SQL:

- Tabelas são como collections

- Colunas são como Maps (Java) ou Dicionários (Python)

***

## Comandos Mongo DB:

### Cread:

- **Criar banco**: 

      Sintaxe: _use_ + _nome_banco_

    | O banco não é criado até existir algum dado nele.

      use pessoasData

- **Adicionar dado em Colections**:

  Sintaxe: _db+_nome_collection__metodo({parametros})_
  
  - Adicionar um elemento: (**insertOne()**) 

        db.pessoas.insertOne({ chave : valor, chave2 : valor2})
  
  - Adicionar vários elemento: (**insertMany()**)
  
     ! Adiciona vários 'Documents' = {} !

        db.pessoas.insertMany([
            {chave1 : valor1, chave1n : valor1n}
            {chave2 : valor2}
            ...
            {chaveN : valorN}
        ])

### Read:

- **Consultar bancos existentes**:

      show dbs

- **Consultar collections existentes**:

      show collections

- **Consultar dados existentes**:

  Sintaxe: _db_ + _nome_collection__metodo()_

  - Retorna todos os dados e informações adicionais:

        db.pessoas.find()

  - Retorna todos os dados em formato Json:

        db.pessoas.find().pretty()

  - Retorna dados especificados na consulta:

        db.pessoas.find({ empregado: true})

  - Retorna a quantidade de elementos:

        db.pessoas.find({ empregado: true}).count()

  - Retorna um elemento (por mais que tenha mais resultados):

        db.pessoas.findOne()

        db.pessoas.findOne({nome:"Joao"}
 
### Update:

- Alterar somente um dado:

      db.pessoas.updateOne({{nome:"João"}, { $set: {esta_empregado: true}})

- Alterar varios dados:

      db.pessoas.updateMany({
            { }, {$set: {chave: valor}

            })

### Delete

- Deletar somente um dado:

      db.deleteOne({ nome:"Josias"})

- Deletar vários dados:

      db.deleteMany({ nome:"Josias"})

- Deletar collections:
  
      db.pessoas.drop()

- Deletar o Banco de Dados:

      db.dropDatabases()

### Operadores:

! Todos os operadores tem $ na frente !

- Maior que **(gt)**:

      db.pessoas.find({idade:{$gt:30}})

- Maior e igual **(gte)**:

      db.pessoas.find({idade:{$gte:30}})

- Menor que **(lt)**:

      db.pessoas.find({idade:{$lt:30}})     

- Menor e igual **(lte)**:

      db.pessoas.find({idade:{$lte :30}})     

- Consulta, atualizando a tabela dos dados retornados:

      db.pessoas.uptadeMany({idade: { $gt: 35} }, {$set:{prioridade: true}})

### Tipos de Dados:

      db.pessoas({
            nome: "Paula",                          /String/
            idade: 35,                              /inteiro/
            hobbies:[ "correr", "Ler","Trilhas" ],  /array/
            esta_trabalhando: true,                 /boolean/
            data_cadastro: new Date()               /salva a data atual/
            caracteristicas: {
                  cor_dos_olhos: "azuis",
                  altura: 1.82,                      /float/
                  perfil: "extrovertida"

            }

      })

      OBS: Usamos o array no caso de vários dados do mesmo tipo. 
      E usamos os documents quando temos dados de vários tipos.

### Tipos de Operadores Update:

- Incremento **(inc)**:

      db.pessoas.updateOne({ nome:"Maria"}, { $inc:{salario:1000}})

- Decremento **(inc)**:

      db.pessoas.updateOne({ nome:"Maria"}, { $inc:{salario: -1000}})

- Indices: 

  - Cria Indices:

    !Criar indices para deixar as consultas mais otimizadas!

        db.pessoas.createIndex({ "nome" : 1})

  - Consulta Indices:

        db.pessoas.getIndexes()

      **winningPlan** = Plano vencedor da consulta, o meio de pesquisa que está sendo mais eficaz na execução.

  - Deletar Indices:
  
        db.pessoas.dropIndex("nome_1")
***

## Comandos CMDER:

- **cls** = limpa a tela
- **mongo** = retorna informações da versão instalada e cria uma conexão.
  
***