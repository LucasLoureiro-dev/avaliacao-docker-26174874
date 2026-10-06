# Respostas · Avaliação Prática de Docker · ViaSerra Transportes (Turma C)

Nome:
Matrícula:
Usuário do GitHub:
Usuário do Docker Hub:

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?
   A imagem base foi a nginx:1.30.5. o tamanho final da imagem do portal ficou com 239.55 Mb 

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.
   O nginx procura geralmente os arquivos do site na pasta/usr/share/nginx/html.
   O comando que eu usei para conferir os arquivos foi o  docker exec -it teste-portal sh, logo depois usei o comando ls -la /usr/share/nginx/html, para conferir se os arquivos foram para la

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.
   Nome da imagem:      lucasloureirodev/viaserra-portal:1.0-26174874
   Link do docker hub:  https://hub.docker.com/r/lucasloureirodev/viaserra-portal

4. Se você mudar o HTML, quais comandos precisa rodar para que a versão nova chegue ao Docker Hub?
   docker build
   docker push

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | rodar o docker build  | a pasta ./pagina nao existe no projeto  | uma falha ao dar o docker build, nao achou a pasta | mudei a pasta do copy de ./pagina para ./site 
| 2 | rodar o container  | o dockerfile tinha uma linha de bash  | o container inicia e logo depois ele para | removi a linha que tinha bash['nginx']
| 3 | ver o projeto rodando  | os arquivos não estavam indo para o local correto  | o site fica com o template do nginx | adicionei o /html na workdir do dokerfile

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?
   A diferença é que o numero da porta geral vem depois do numero da porta do container, sendo porta-container:porta-geral


## Parte 4 · Primeiro docker-compose

7. Escreva os dois comandos `docker run` que fariam o mesmo que o seu `docker-compose.yml`.
   manutencao docker run -d --name manut -p 7074:80 manutencao:2617487
   portal docker run -d --name teste-portal -p 8074:80 lucasloureirodev/viaserra-portal:1.0-2617487

8. Qual comando derruba os dois containers de uma vez?
   docker compose stop

## Verificador

9. Código de conclusão impresso pelo verificador:

```
================================================================
 Verificador · Avaliação Prática de Docker · Turma C
================================================================
 Matrícula 26174874 · portal 8074 · manutenção 7074

A. Arquivos e Git
[ OK ] A1 portal/Dockerfile segue os requisitos
[ OK ] A2 .env fora do Git e .env.example versionado
[ OK ] A3 4+ commits e remoto no GitHub (encontrados: 6)
[ OK ] A4 imagem lucasloureirodev/viaserra-portal:1.0-26174874 pública no Docker Hub

B. docker compose
         (ainda há lacunas ____ no docker-compose.yml)
[ OK ] B1 serviços portal e manutencao em execução
[ OK ] B2 portal roda a imagem publicada
[ OK ] B3 portas: portal em 8074 e manutenção em 7074

C. Conteúdo
[ OK ] C1 portal mostra seu nome e sua matrícula
[ OK ] C2 página de manutenção servindo o aviso "Voltamos em breve"

================================================================
 Resultado: 9/9 verificações
 Código de conclusão: VIASERRA-26174874-1FDC1C57
 Copie o código para o respostas.md, tire o print desta tela e faça o commit final.
================================================================
```
