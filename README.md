# fastapi-challenge

TESTE TÉCNICO DESENVOLVEDORA LARISSA NÉRI

# Regras Importantes:

-   Só serão aceitos arquivos dos tipos .txt, .exe, .zip, .csv, .xlsx e .png.
-   Para cada tipo de arquivo, há um limite de tamanho específico: .txt (5MB), .exe (10MB), .zip (25MB), .csv (2MB), .xlsx (5MB) e .png (1MB).
-   Os usuários devem estar previamente cadastrados e aprovados para fazer upload de imagens.
-   É necessário manter um histórico de arquivos submetidos para análise de possíveis arquivos maliciosos ou impróprios.
-   O sistema deve registrar logs de falhas/exceções em tempo real para facilitar a análise técnica.

## Arquitetura:

Para criar o sistema de upload e compartilhamento de imagens, eu utilizaria o framework FastAPI em Python para criar a API. O FastAPI é uma ferramenta leve e flexível que permite criar aplicações web rapidamente.

Para armazenar as imagens, eu utilizaria o Amazon S3 (Simple Storage Service). O S3 é uma solução de armazenamento na nuvem escalável e de alta disponibilidade, que permite gerar links compartilháveis para os arquivos armazenados.

Para o banco de dados, eu utilizaria o PostgreSQL. O PostgreSQL é um sistema de gerenciamento de banco de dados relacional de código aberto, que é robusto e escalável.

## As tabelas principais seriam:

-   *Usuários:* armazena as informações dos usuários, incluindo o nome, o e-mail, a senha, a data de nascimento e o gênero.
-   *Arquivos:* armazena as informações dos arquivos, incluindo o nome, o tipo, o tamanho, o usuário que o enviou e o link compartilhável.
-   *Análises de usuários:* armazena as análises realizadas pelos usuários internos para aprovar ou rejeitar os usuários externos.

A autenticação da aplicação seria realizada através de tokens JWT (JSON Web Token). Os tokens seriam gerados após a autenticação bem-sucedida do usuário e incluiriam as informações de autorização do usuário.

Para garantir que apenas usuários internos possam aprovar outros usuários, eu adicionaria uma flag "interno" à tabela de usuários. A flag seria atribuída a cada usuário interno durante o processo de cadastro e seria verificada antes de permitir que o usuário realizasse análises de outros usuários. Dessa forma, apenas usuários com a flag "interno" atribuída poderiam aprovar ou rejeitar usuários externos.

## Endpoints:

-   POST /usuarios: permite que os usuários se cadastrem na aplicação. Esse endpoint deve receber as informações de nome, e-mail, senha, data de nascimento e gênero do usuário e retornar um token JWT para autenticação.
-   POST /auth: permite que os usuários façam login na aplicação. Esse endpoint deve receber o e-mail e a senha do usuário e retornar um token JWT para autenticação.
-   POST /arquivos: permite que os usuários façam upload de arquivos. Esse endpoint deve receber o arquivo e as informações do usuário (através do token JWT) e retornar um link compartilhável para o arquivo.
-   GET /arquivos: permite que os usuários vejam a lista de arquivos submetidos. Esse endpoint deve retornar uma lista de arquivos com o nome, o tipo, o tamanho, o usuário que o enviou e o link compartilhável.
-   POST /analise-usuarios: permite que os usuários internos façam análise de usuários externos. Esse endpoint deve receber o e-mail do usuário a ser analisado e a decisão de aprovação ou rejeição (através do token JWT).

## Planejamento
Planejamento:

1.  Definição do projeto:
    
    -   Realizar uma análise do problema e das necessidades do usuário para definir as funcionalidades e requisitos da aplicação.
    -   Elaborar uma documentação com as regras importantes e a arquitetura planejada para o projeto.
    -   Criar um plano de projeto para organizar o desenvolvimento.
2.  Configuração do ambiente de desenvolvimento:
    
    -   Instalar o Python e o FastAPI no ambiente de desenvolvimento.
    -   Realizar o setup do PostgreSQL e criar o banco de dados inicial.
    -   Configurar o Amazon S3 para armazenamento das imagens.
3.  Desenvolvimento da API:
    
    -   Semana 1: Desenvolver os endpoints de cadastro e login de usuários.
    -   Semana 2: Desenvolver o endpoint de upload de arquivos.
    -   Semana 3: Desenvolver o endpoint de listagem de arquivos.
    -   Semana 4: Desenvolver o endpoint de análise de usuários.
4.  Testes e validação:
    
    -   Realizar testes de unidade e integração da API para garantir sua funcionalidade.
    -   Realizar testes de performance para verificar o desempenho da aplicação.
    -   Realizar testes de usabilidade para garantir a facilidade de uso da aplicação pelos usuários.
5.  Implantação e manutenção:
    
    -   Realizar o deploy da aplicação em um servidor de produção.
    -   Realizar monitoramento da aplicação para garantir sua disponibilidade e performance.
    -   Realizar manutenção periódica da aplicação para correção de bugs e adição de novas funcionalidades.
