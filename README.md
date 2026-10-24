# PHP2Shell: prompt para corrigir servidores com o Claude Code

[English version](README.en.md)

Um prompt pronto a copiar para quem tem o [Claude Code](https://code.claude.com/docs/en/overview) num servidor (ou ligado a ele por SSH) e quer verificar e corrigir as falhas **PHP2Shell** do PHP (CVE-2026-109618 e CVE-2026-109619), com a ajuda do Claude Code e sob o seu controlo.

Versão 1.0 · 24 de outubro de 2026

## O que o prompt faz

O prompt obriga o Claude Code a trabalhar por fases e a pedir autorização antes de qualquer alteração:

1. **Inventário, só leitura:** encontra todas as instalações de PHP (linha de comandos, PHP-FPM, Apache com mod_php, Docker, painéis) e diz se cada uma já está corrigida.
2. **Verificação básica de intrusão, só leitura:** procura sinais de ataque desde 17 de outubro de 2026. Se encontrar algum, para e recomenda isolar o servidor.
3. **Plano:** propõe os passos para aquele servidor, do mais rápido e seguro para o mais demorado, e espera pela tua aprovação.
4. **Alterações, uma de cada vez:** cada comando é mostrado e só corre depois do teu "sim". Os ficheiros de configuração são copiados antes de serem alterados.
5. **Verificação e relatório:** confirma o resultado e entrega uma tabela antes e depois.

O prompt também proíbe o Claude Code de usar correções não oficiais, de apagar ficheiros, de mexer no código da aplicação e de obedecer a instruções escritas em ficheiros ou logs do servidor, que num servidor atacado podem ter sido deixadas pelo atacante.

## Como usar

1. Lê o [aviso de responsabilidade](#aviso-de-responsabilidade) abaixo.
2. Faz uma cópia de segurança ou um snapshot do servidor. Se puderes, começa por um servidor de testes.
3. Abre o Claude Code no servidor, ou num computador ligado ao servidor por SSH.
4. Confirma que o Claude Code está no modo **Manual** (o modo por omissão), em que pede autorização antes de comandos que alteram o sistema. **Não uses os modos Auto, Accept edits nem Bypass permissions**, e não escolhas a opção "não perguntar outra vez" para comandos que alteram o servidor.
5. Abre o [PROMPT.pt.md](PROMPT.pt.md), copia tudo o que está entre as duas linhas e cola no Claude Code.
6. Lê cada comando antes de o aprovares. Se não perceberes um comando, pergunta ao Claude Code o que ele faz antes de dizeres "sim".

## O que este prompt não faz

- Não protege servidores que não consegue ver: contentores noutras máquinas, alojamento partilhado sem acesso ao terminal, WAF ou fornecedores externos. Esses passos ficam no relatório final para fazeres à mão.
- Não migra aplicações de PHP 8.1 ou anterior para versões novas. Apresenta as opções e para.
- Não investiga a fundo um servidor comprometido. Se houver sinais de intrusão, a recomendação é isolar o servidor e pedir ajuda especializada.

## Aviso de responsabilidade

Este prompt é fornecido "tal como está", sem garantias de qualquer tipo, expressas ou implícitas. Não garante que o servidor fique seguro, que a correção funcione no teu ambiente nem que não haja erros ou interrupções do serviço.

A decisão de o usar, e a responsabilidade por tudo o que for executado no teu sistema, são inteiramente tuas. O Claude Code é uma ferramenta de inteligência artificial e pode cometer erros: lê e aprova cada comando antes de ele ser executado.

Testa primeiro num ambiente de testes, faz uma cópia de segurança ou snapshot antes de começar e não uses modos de aprovação automática. Segue as políticas da tua organização sobre o uso de ferramentas de IA em servidores.

As informações sobre versões e medidas temporárias refletem as fontes oficiais à data indicada e podem mudar. Confirma sempre os avisos oficiais do PHP e da tua distribuição.

Este projeto não é afiliado ao projeto PHP, à Anthropic nem a nenhum fornecedor citado.

## Fontes oficiais

- [PHP: avisos de segurança de 21 e 23 de outubro de 2026](https://www.php.net/archive/2026.php)
- [PHP: aviso técnico da CVE-2026-109618](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w)
- [PHP: aviso técnico da CVE-2026-109619](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp)
- [CERT-EU: Security Advisory 2026-018](https://cert.europa.eu/publications/security-advisories/2026-018/)
- [Red Hat: boletim RHSB-2026-013](https://access.redhat.com/security/vulnerabilities/RHSB-2026-013)
- [Ubuntu: CVE-2026-109618](https://ubuntu.com/security/CVE-2026-109618)
- [Debian: CVE-2026-109618](https://security-tracker.debian.org/tracker/CVE-2026-109618)
- [Manual do PHP: alterar a configuração](https://www.php.net/manual/en/configuration.changes.php)
- [Claude Code: permissões e modos](https://code.claude.com/docs/en/permissions)

## Histórico de versões

- **1.0 (24 de outubro de 2026):** primeira versão.
