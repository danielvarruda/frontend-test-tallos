# APLICAÇÃO DO TEST TALLOS
## _Aplicação desenvolvida para uma entrevista na Tallos_

## Tecnologias utilizadas:

- Vue
- Vuex
- NPM
- Docker

## Instalação

A aplicação é baseada em Vue, logo é necessário possuir em sua máquina o software Node JS e o pacote Vue.

Contudo, devido a conteinerização aplicada nessa aplicação é possível simplificar esse passo. Basta rodar o comando abaixo e o docker fará seu trabalho.

```sh
docker-compose up --build
```

Mas caso não deseje usar o composer, e tenha o vue configuarado em sua máquina:

```sh
npm install && npm run serve
```

A pasta node_modules fica dentro do docker pra facilitar a instalação. Logo ela não é criada em sua máquina local. Isso pode gerar alguns erros de importação em sua IDE, mas é algo apenas visual. Caso queira que tudo funcione sem incomodos instale o node j e vue em sua máquina. 

```sh
docker cp teste-tallos:/app/node_modules/. ./node_modules)
```

A Aplicação rodará em:

```sh
127.0.0.1:8080 ou localhost:8080
```

## License
**Software Livre, Divirta-se!**
