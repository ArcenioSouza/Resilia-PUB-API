# Resilia-PUB API

O Resilia-PUB é uma API Rest de gerenciamento de PUBS construída em colaboração com [@Matheus Camba](https://github.com/MatheusCamba), [@Hugo Parada](https://github.com/haparada9), [@Milena Souza](https://github.com/Milena2712) e [@Gicelle Sena](https://github.com/Gicelle-sena). Cada colaborador ficou responsável por criar uma instância do banco de dados da API e posteriormente iremos usar os conhecimentos obtidos para juntarmos todas as instâncias e criar os seus relacionamentos. Com essa aplicação você será capaz de salvar, atualizar, pesquisar e deletar registros de funcionários do PUB. 

# Ferramentas utilizadas

<div>
   <img width='50px' height='50px' src='https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/nodejs/nodejs-original.svg'>
   <img width='50px' height='50px' style="margin: 5px" src='https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/npm/npm-original-wordmark.svg'>
   <img width='50px' height='50px' style="margin: 5px" src='https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-plain.svg'>
   <img width='50px' height='50px' style="background-color: #FFF; margin: 5px" src='https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/markdown/markdown-original.svg'>
   <img width='100px' height='50px' style="background-color: #FFF; margin: 5px" src='https://upload.wikimedia.org/wikipedia/commons/thumb/3/38/SQLite370.svg/382px-SQLite370.svg.png'>
   <img width='50px' height='50px' style="margin: 5px" src='https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/vscode/vscode-original.svg'>
   <img width='50px' height='50px' style="margin: 5px" src='https://cdn.freelogovectors.net/wp-content/uploads/2020/12/postman-logo.png'>
</div>


# Como utilizar a aplicação

### **1 - Faça o clone do repositório**

Para fazer o clone desse repositório basta copiar o código abaixo e colar em seu terminal.
```
git clone https://github.com/ArcenioSouza/Resilia-PUB.git
```

### **2 - Instale as dependencias necessárias**

Para instalar as dependencias entre na pasta Resilia-PUB usando o comando:
```
cd Resilia-PUB
```
Após o terminal entrar na pasta execute o comando abaixo para instalar todas as dependencias necessárias para execução da aplicação.
```
npm install
```

### **3 - Execute a aplicação**

Para executar a aplicação basta executar o comando abaixo em seu terminal.
```
npm start
```
**Observação:** Essa aplicação será executada por padrão na porta 3000 do seu localHost, caso essa porta esteja sendo utilizada por outra aplicação basta mudar o valor da variável 'port' do arquivo 'app.js' para um valor de porta disponível em seu sistema.

# Rotas da API

Essa aplicação possui um conjunto de rotas que torna possível o uso de todos os verbos HTTP necessários para a realização do CRUD.

### **1 - Salvar as informações de um funcionário**

Para salvar um funcionário na API é usado o método HTTP `POST` no caminho `urlApi/employee`.

Deverá ser passado no corpo da requisição as informações do funcionário em formato JSON segundo o modelo e propriedades abaixo:
```
{
   "name": "Arcenio Souza",
   "office": "Gerente",
   "wage": 10000,
   "cpf": 33132382801
}
``` 
As informações de cadastro de funcionários passam por validações antes de serem salvas no banco de dados, portanto algumas regras no preenchimento das informações devem ser seguidas:

**Regras para nome(name)**
- Deve ter as iniciais em letras maiúsculas e restante em letras minúsculas;
- Não pode haver espaços duplos entre as nomes;
- Não pode haver espaço no inicio ou final do nome;

**Regras para cargo(office)**
- Os cargos permitidos na empresa são: "Gerente", "Garçon", "Copeiro", "Barman", "Cozinheiro" e "Auxiliar de Cozinha". Qualquer cargo diferente desses não serão permitidos;

**Regras para salario(wage)**
- Os valores não devem conter letras ou cifrões;
- Se o valor possuir casas decimais a separação ao digitar deve ser feita com ".";

**Regras para CPF**
- O numero deve ser válido segundo as regras de validação de CPF da Receita Federal que podem ser consultadas através desse link [Como é feita a validação do um CPF](https://www.calculadorafacil.com.br/computacao/validar-cpf)


### **2 - Atualizar as informações de um funcionário**

Para atualizar as informações um funcionário na API é usado o método HTTP `PUT` no caminho `urlApi/employee/:id`.

Deverá ser passado como parâmetro um id existente no banco de dados na url da requisição e no corpo da requisição as informações do funcionário em formato JSON segundo o modelo e propriedades abaixo:
```
{
   "name": "Arcenio Souza",
   "office": "Gerente",
   "wage": 10000,
   "cpf": 33132382801
}
``` 
Assim como para salvar as informações de um funcionário, os dados para atualização das informações também passam pelas mesmas validações descritas no tópico anterior.

### **3 - Deletar as informações de um funcionário**

Para deletar as informações um funcionário na API é usado o método HTTP `DELETE` no caminho `urlApi/employee/:id`.

Deverá ser passado como parâmetro um id existente no banco de dados na url da requisição.

### **4 - Buscar as informações de apenas um funcionário**

Para buscar as informações um funcionário na API é usado o método HTTP `GET` no caminho `urlApi/employee/:id`.

Deverá ser passado como parâmetro um id existente no banco de dados na url da requisição e a API retornará os dados do funcionário em formato JSON como o exemplo a seguir:

`http://localhost:3000/employee/2`
```
{
    "id": 2,
    "name": "José Oliveira",
    "office": "Copeiro",
    "wage": 2500.7,
    "cpf": 21256877929
}
```

### **4 - Buscar as informações de todos os funcionários**

Para buscar as informações de todos os funcionários na API é usado o método HTTP `GET` no caminho `urlApi/employees`.

A API retornará um array de objetos em formato JSON como o exemplo abaixo:
```
[
    {
        "id": 1,
        "name": "Arcenio Souza",
        "office": "Gerente",
        "wage": 50000,
        "cpf": 67346720008
    },
    {
        "id": 2,
        "name": "José Oliveira",
        "office": "Copeiro",
        "wage": 2500.7,
        "cpf": 93009185081
    },
    {
        "id": 3,
        "name": "Marcos André",
        "office": "Garçon",
        "wage": 1800,
        "cpf": 55855978095
    },
    {
        "id": 4,
        "name": "Francisco Junior",
        "office": "Auxiliar de Cozinha",
        "wage": 1800,
        "cpf": 22789188009
    },
    {
        "id": 5,
        "name": "Weber Caetano",
        "office": "Barman",
        "wage": 2100.55,
        "cpf": 37842561044
    }
]
```

# Créditos

Ao professor [@LéoCosta](https://github.com/LeoCosta-dev) pelos ensinamentos e pelo apoio constante em aula e fora de aula para a realização desse projeto.

Ao meu grupo pelo empenho diário na realização desse projeto. E a [Resilia Educação](https://www.resilia.com.br/) que tem proporcionado tarefas que agregam conhecimentos valiosos a minha formação.
