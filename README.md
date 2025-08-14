Este projeto consiste na instalação e configuração de um ambiente completo para WordPress em um servidor Linux.
O passo a passo inclui a preparação do servidor, instalação de dependências, configuração do Apache e PHP, criação do banco de dados com MariaDB, deploy do WordPress, configuração de SSL com Let’s Encrypt e integração com Git para versionamento do código.

O objetivo é permitir que qualquer usuário com acesso ao servidor possa replicar a configuração de forma segura, escalável e com boas práticas de administração.

Passo a Passo Técnico e Funcional
1. Preparação do Servidor

Atualização do sistema e instalação de pacotes essenciais (apache2, php, mariadb, git, certbot).

Habilitação de módulos do Apache necessários para WordPress (rewrite, ssl, headers).

Configuração de swap para otimizar servidores com memória limitada.

2. Configuração do Git

Criação de repositório bare no servidor (~/app_bare) para versionamento centralizado.

Criação de repositório de aplicação (~/app_repo) que será sincronizado com o bare.

Integração com repositórios locais para facilitar deploy e atualizações via Git.

3. Deploy do WordPress

Download da versão mais recente do WordPress via curl.

Extração e organização dos arquivos dentro da pasta wordpress_site.

Ajuste de permissões para o usuário do Apache (www-data), garantindo segurança e funcionamento correto.

4. Configuração do Banco de Dados (MariaDB)

Criação do banco de dados específico para o WordPress.

Criação de usuário com privilégios completos sobre este banco.

Inserção das credenciais no wp-config.php para conectar o WordPress à base de dados.

5. Configuração do PHP

Ajuste de limites de upload, memória e tempo de execução.

Habilitação de extensões essenciais (pdo_sqlite, sqlite3, curl, mbstring, etc).

Reinício do Apache para aplicar mudanças.

6. Configuração do Apache

Criação de arquivos de site (.conf) para HTTP e HTTPS.

Configuração de redirecionamento automático de HTTP para HTTPS.

Permissão para .htaccess controlar URLs amigáveis e redirecionamentos.

Inclusão de diretório .well-known/acme-challenge para renovação automática de SSL.

7. Certificados SSL (Let’s Encrypt)

Emissão de certificados SSL válidos para o domínio.

Configuração de HTTPS no Apache.

Agendamento automático de renovação via Certbot para manter segurança contínua.

8. Otimização do Banco de Dados e Servidor

Ajuste de parâmetros do MariaDB para servidores com RAM limitada.

Criação de swap para evitar problemas de memória durante execuções pesadas.

Limitação de conexões e tamanho de cache para performance otimizada.

9. Segurança e Sessões do WordPress

Forçar uso de HTTPS no painel administrativo (wp-admin).

Configuração de cookies e duração de login prolongado para melhorar a experiência do usuário.

Resumo Técnico

Servidor: Linux (Ubuntu/Debian)

Webserver: Apache2 com módulos rewrite, ssl e headers

Banco de Dados: MariaDB

PHP: com extensões essenciais para WordPress

Deploy: via Git para versionamento e sincronização

SSL: Certbot / Let’s Encrypt para HTTPS

Segurança: HTTPS obrigatório, permissões corretas, otimização de memória e banco de dados

Observações

Todo o processo é reproduzível e modular, podendo ser adaptado para múltiplos domínios.

Permite integração com Git para deploy contínuo.

Suporta configurações de segurança e performance adequadas para sites WordPress profissionais.
