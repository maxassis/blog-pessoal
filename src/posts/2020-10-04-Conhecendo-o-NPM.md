---
date: 2020-10-04 21:34:23
title: Conhecendo o NPM
description: O Gerenciador de Pacotes do Nodejs
category: npm
background: "#f0f3bd"
---



# Conhecendo o NPM – Gerenciador de pacotes para Nodejs



*O NPM (Node Package Manager) consiste muito mais em um kit de ferramentas para desenvolvimento do que somente um instalador de pacotes.*
Confira alguns termos importantes da hospedagem nodejs.

O **Node.js** é uma tecnologia, uma plataforma que utiliza o JavaScript como sintaxe. É de código aberto e possui uma ampla comunidade. Através dele, é possível desenvolver pequenas e grandes aplicações.

O Node utiliza o NPM como gerenciador de pacotes e bibliotecas, que por sua vez é o maior ecossistema de bibliotecas open source do mundo. Site oficial: https://nodejs.org/en/



## NPM

O NPM consiste muito mais em um kit de ferramentas para desenvolvimento do que somente um instalador de pacotes. Através do `npm config` é possível realizar uma série de tarefas, como efetuar o login/logout do npm.org para controlar pacotes próprios por exemplo. Enquanto isso, através de um arquivo .npmrc é possível ter acesso as configurações diretamente para uso no shell, interagindo automaticamente com o binário sem a necessidade de enviar parâmetros extras. Com o .npmrc, é possível ter configurações exclusivas para diferentes projetos em uso, o que torna a solução flexível para quando se possui diversos ambientes/projetos simultâneos. Através do npm config também são feitas configurações padrões com o comando para nomes de autoria, licença de software e outras informações.



[![img](https://king.host/wiki/wp-content/uploads/2016/10/npm.png)](https://king.host/wiki/wp-content/uploads/2016/10/npm.png)



## Alguns comandos úteis

Com o `npm dist-tag` é possível gerar a nomenclatura de múltiplas releases do módulo, fazendo que seja possível gerar um branch release e outro testing, facilitando o controle de branchs diferentes na publicação dos módulos. Por padrão, o npm adicionará a tag *@latest* e é esta a versão baixada quando um módulo é instalado. O npm em si segue esse padrão no próprio npm, gerando tags conforme a necessidade, tags chamadas *next* são usadas para controlar os próximos releases, permitindo os usuários a testarem as novas versões antes do lançamento oficial como *latest* que é considerada a versão stable (até mesmo a versão LTS possui uma versão next de upgrade).



## Dependências

O comando `npm shrinkwrap` cria a lista de dependências de uma app, gerando um arquivo chamado *npm-shrinkwrap.json* que pode ser lido para facilitar a reprodução do ambiente e, ao mesmo tempo, garantir versões específicas do módulo do projeto. O shrinkwrap não usa cache também, fazendo com que você sempre baixe os módulos do repositório em uma forma de reprodução mais real. Por não usar cache, o build completo pode falhar por causa de apenas um módulo que está nas dependências e falhou. Usando `npm instal --save --save-bundle`, o *buildDependencies* irá gerar o package.json quando se faz um *npm publish*, gerando uma redução no consumo da rede e reduzindo o tempo de instalação.



## Controle

Para controlar os módulos de maneira mais prática em redes com velocidade baixa, é possível fazer um `npm config get cache` para verificar em qual diretório o cache está sendo armazenado, `npm cache rm` é usado para remover caches de módulos que você já baixou (os módulos nunca são removidos se não solicitado) e para limpar todos os módulos instalados, pode-se usar o comando `npm cache clear`. Com o `npm install --cache-min=999999` é possível dizer para o npm que os últimos módulos instalados disponíveis devem ser usados.