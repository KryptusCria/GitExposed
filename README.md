# GitExposed
Encontrando GitExposed 


. Primeiro passo varre portas no endereço ip
    
1. usar wfuzz com lista common.txt
    
2.  git- clone [https://github.com/v0re/dirb/blob/master/wordlists/common.txt](https://github.com/v0re/dirb/blob/master/wordlists/common.txt)
    

wfuzz -c -z file,(wordlist”)  --hh 404 <http:// ip do site>/FUZZ

Neste comando a opçao - -hh faz com que o wfuzz ignore o numero de palavras ou caracteres retornados pela resposta HTTP 404. Ou seja se a resposta HTTO 404 tiver um corpo de resposta especifico (como uma pagina de erro personalizada) o wfuzz não levara em cosideração o tamanho do corpo de resposta ao filtrar os resultados 

wfuzz -c -z file,(wordlist”)  --hc 404 <http:// ip do site>/FUZZ

--hc 404 faz com quem o wfuzz ignore as respostas que retornaram o código de status HTTP 404(Not Found). isso signidfica que ele não exibira resultados onde a resposta do servidoe é 404
  

Para lista diretórios e pastas do site 
  

1. Após encontra o diretório /.git/ iremos baixar para nossa maquina usando a ferramenta git_dumper [https://github.com/arthaud/git-dumper](https://github.com/arthaud/git-dumper)
    
Comando para roda o git-dumper
python3 git_dumper.py http:// IP da maquina / " nome do arquivo "

Apos dar um dumper na nossa maquina iremos abrir o index.php

Entraremos dentro da pasta git log

E daremos um git show no hash ☢️

✅ Contramedidas para Prevenir a Exposição do.git
1️⃣ Bloqueio de Acesso ao Diretório .gitno Servidor Web
A forma mais eficaz de prevenir a exposição é configurar o servidor para impedir o acesso ao diretório .git.

Para Apache ( .htaccess):
apache
RewriteEngine on
RewriteRule ^(.*/)?\.git/ - [F,L]
Para Nginx:
nginx


location ~ /.git {
    deny all;
    return 403;
}

2️⃣ Remover Diretório .gitdo Servidor de Produção
Se o código já estiver implantado, o diretório .gitnão precisa estar presente no servidor. Você pode removê-lo com:

sh
rm -rf /caminho/do/site/.git

3️⃣ Uso de .gitignorepara Evitar Upload Acidental
Se o código-fonte estiver sendo versionado dentro de um repositório maior, adicione uma regra para ignorar o .gitnão .gitignore:

/.git

4️⃣ Verificação Regular com Ferramentas de Segurança
Use ferramentas como:

GitRob – Analise repositórios em busca de informações confidenciais.
GitLeaks – Detecta credenciais






