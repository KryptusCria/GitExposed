# GitExposed
✅ Vulnerabilidade de Exposição de Repositório Git (.git exposed)
O que é:

A vulnerabilidade de exposição de repositório Git, também conhecida como .git exposed, ocorre quando a pasta .git de um projeto, que contém informações sensíveis sobre o histórico de的版本控制, metadados e arquivos de configuração, é acessível publicamente através da web. Isso pode acontecer devido a erros de configuração do servidor web, permissões incorretas ou falta de proteção adequada.

Como encontrar:

Mapeamento de subdomínios: Utilize ferramentas como sublist3r, assetfinder ou serviços online para descobrir subdomínios e URLs relacionados à empresa.

Detecção de diretórios .git: Utilize ferramentas como dirsearch, ffuf ou scripts personalizados para verificar se a pasta .git está acessível em URLs como http://exemplo.com/.git/ ou http://exemplo.com/repositorio/.git/.

Análise de robôs.txt: Verifique o arquivo robots.txt para identificar possíveis diretórios ou arquivos sensíveis que possam estar expostos.

Ferramentas de varredura: Utilize ferramentas de varredura de vulnerabilidades como Nessus, OpenVAS ou Acunetix para identificar automaticamente exposições de repositórios Git.

Criticidade:

A criticidade dessa vulnerabilidade é considerada alta, pois a pasta .git exposta pode conter informações extremamente sensíveis, como:

Código fonte: O código fonte completo do projeto pode ser acessado, permitindo que atacantes encontrem vulnerabilidades, compreendam a lógica do sistema e explorem falhas de segurança.
Histórico de commits: O histórico de commits revela informações sobre as alterações no código, autores, datas e mensagens, o que pode ser usado para obter informações sobre a equipe de desenvolvimento, processos internos e possíveis pontos fracos.
Credenciais de acesso: Arquivos de configuração podem conter credenciais de acesso a bancos de dados, APIs, servidores e outros recursos, permitindo que atacantes obtenham acesso não autorizado a sistemas críticos.
Variáveis de ambiente: Variáveis de ambiente podem conter informações sensíveis, como chaves de API, senhas e configurações de produção, que podem ser exploradas por atacantes.
Contramedidas:

Bloqueio de acesso: Configure o servidor web para bloquear o acesso à pasta .git através de regras de firewall, arquivos .htaccess ou configurações do servidor.

Remoção da pasta .git: Remova a pasta .git do diretório web do servidor, caso ela não seja necessária para o funcionamento do sistema.

Proteção de arquivos de configuração: Criptografe ou proteja com permissões restritas os arquivos de configuração que contêm informações sensíveis, como credenciais de acesso.

Utilização de ferramentas de controle de versão: Utilize ferramentas de controle de versão como Gitlab, Github ou Bitbucket para hospedar os repositórios de código de forma segura, fora do diretório web do servidor.

Auditoria de segurança: Realize auditorias de segurança periódicas para identificar e corrigir possíveis vulnerabilidades, incluindo exposições de repositórios Git.

Treinamento de conscientização: Treine os desenvolvedores e equipes de TI sobre os riscos de exposição de repositórios Git e as melhores práticas de segurança para proteger informações sensíveis.

Impacto em caso de ataque:

Uma empresa que sofre um ataque de Git exposed pode ter diversos impactos negativos, como:

Vazamento de dados: Informações sensíveis, como código fonte, credenciais de acesso e dados de clientes, podem ser expostas e utilizadas por atacantes para fins maliciosos.
Comprometimento de sistemas: Atacantes podem obter acesso não autorizado a sistemas críticos, como servidores, bancos de dados e APIs, explorando vulnerabilidades encontradas no código fonte ou utilizando credenciais vazadas.
Interrupção de serviços: Atacantes podem causar interrupções de serviços, como indisponibilidade de websites, sistemas internos ou APIs, afetando a operação da empresa e a experiência dos clientes.
Danos à reputação: A exposição de informações sensíveis e o comprometimento de sistemas podem causar danos à reputação da empresa, resultando em perda de clientes, processos judiciais e sanções regulatórias.


Como encontrala.

🔴 Primeiro passo varrer portas no endereço ip
    
1. usar wfuzz com lista common.txt
    
2.  git- clone [https://github.com/v0re/dirb/blob/master/wordlists/common.txt](https://github.com/v0re/dirb/blob/master/wordlists/common.txt)
    

wfuzz -c -z file,(wordlist”)  --hh 404 <http:// ip do site>/FUZZ

Neste comando a opçao - -hh faz com que o wfuzz ignore o numero de palavras ou caracteres retornados pela resposta HTTP 404. Ou seja se a resposta HTTP 404 tiver um corpo de resposta especifico (como uma pagina de erro personalizada) o wfuzz não levara em cosideração o tamanho do corpo de resposta ao filtrar os resultados 

wfuzz -c -z file,(wordlist”)  --hc 404 <http:// ip do site>/FUZZ

--hc 404 faz com quem o wfuzz ignore as respostas que retornaram o código de status HTTP 404(Not Found). isso signidfica que ele não exibira resultados onde a resposta do servidoe é 404
  

Para lista diretórios e pastas do site 
  

1. Após encontra o diretório /.git/ iremos baixar para nossa maquina usando a ferramenta git_dumper [https://github.com/arthaud/git-dumper](https://github.com/arthaud/git-dumper)
    
Comando para roda o git-dumper
python3 git_dumper.py http:// IP da maquina / " nome do arquivo "

Apos dar um dumper na nossa maquina iremos abrir o index.php

Entraremos dentro da pasta git log

E daremos um git show no hash ☢️




