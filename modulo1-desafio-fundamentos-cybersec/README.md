# Módulo 1 – Fundamentos de Cybersecurity  
## Desafio: Mapeamento de Rede Corporativa

Relatório técnico desenvolvido como parte do **Módulo 1 – Fundamentos de Cybersecurity** da formação em Cibersegurança (Kensei & Vai na Web).

---

## Informações do Relatório

- **Autor:** Yuri Cordeiro  
- **Data:** 24/07/2025  
- **Versão:** 1.0  
- **Tipo:** Relatório Técnico de Reconhecimento de Rede  

---

## 1. Sumário Executivo

Foi realizada uma análise de reconhecimento em um ambiente simulado de **rede corporativa segmentada**, composta por três sub-redes distintas.  
O objetivo principal foi **mapear ativos**, **identificar serviços expostos**, **avaliar riscos** e **validar a segmentação de rede**.

Durante a análise, foram identificados diversos servidores expostos na rede de infraestrutura, estações de trabalho sem serviços acessíveis diretamente e dispositivos pessoais isolados em uma rede guest.

---

## 2. Objetivo

Analisar a rede simulada com o intuito de:
- Identificar ativos e serviços acessíveis
- Detectar possíveis falhas de segmentação
- Avaliar riscos de exposição
- Produzir recomendações técnicas para mitigação de riscos

---

## 3. Escopo

### Ambiente
- Ambiente simulado utilizando **Docker**
- Redes segmentadas:
  - `corp_net` – 10.10.10.0/24
  - `infra_net` – 10.10.30.0/24
  - `guest_net` – 10.10.50.0/24

### Máquina de Análise
- IPs atribuídos:
  - 10.10.10.2
  - 10.10.30.2
  - 10.10.50.4

### Ferramentas Utilizadas
- `nmap`
- `arp-scan`
- `ip a`
- `ping`
- `dig`
- Draw.io (diagrama de rede)

---

## 4. Metodologia

As seguintes etapas foram executadas:

1. Identificação das interfaces de rede (`ip a`)
2. Descoberta de hosts ativos (`nmap -sn`)
3. Varredura de serviços e versões (`nmap -sS -sV`)
4. Mapeamento de IPs, serviços e funções
5. Criação de diagrama de rede com relações e segmentação
6. Análise de riscos e exposição de serviços

---

## 5. Diagrama da Rede

O diagrama da rede foi criado no **Draw.io**, representando:
- Sub-redes
- Hosts
- IPs
- Serviços expostos
- Relações entre os ativos

Arquivo: `projeto-final-kensei.xml`

---

## 6. Diagnóstico (Achados)

### corp_net (10.10.10.0/24)

| Host | IP | Portas | Função |
|-----|----|-------|--------|
| WS_001 | 10.10.10.10 | Nenhuma | Estação de trabalho |
| WS_002 | 10.10.10.101 | Nenhuma | Estação de trabalho |
| WS_003 | 10.10.10.127 | Nenhuma | Estação de trabalho |
| WS_004 | 10.10.10.222 | Nenhuma | Estação de trabalho |
| Gateway | 10.10.10.1 | 111/tcp | Gateway |

---

### infra_net (10.10.30.0/24)

| Host | IP | Porta | Função |
|----|----|------|-------|
| FTP Server | 10.10.30.10 | 21/tcp | Servidor FTP |
| MySQL Server | 10.10.30.11 | 3306/tcp | Banco de Dados |
| Samba Server | 10.10.30.15 | 139, 445 | Compartilhamento SMB |
| OpenLDAP | 10.10.30.17 | 389, 636 | Autenticação |
| Zabbix Server | 10.10.30.117 | 80/tcp | Monitoramento |
| Legacy Server | 10.10.30.227 | Nenhuma | Servidor legado |
| Gateway | 10.10.30.1 | 111/tcp | Gateway |

---

### guest_net (10.10.50.0/24)

| Host | IP | Portas | Função |
|----|----|-------|-------|
| notebook-carlos | 10.10.50.2 | Nenhuma | Dispositivo pessoal |
| laptop-vastro | 10.10.50.3 | Nenhuma | Dispositivo pessoal |
| macbook-aline | 10.10.50.5 | Nenhuma | Dispositivo pessoal |
| laptop-luiz | 10.10.50.6 | Nenhuma | Dispositivo pessoal |
| Gateway | 10.10.50.1 | 111/tcp | Gateway |

---

## 7. Recomendações

- Desativar o serviço FTP
- Restringir acesso ao MySQL apenas a IPs autorizados
- Revisar compartilhamentos SMB
- Monitorar acessos à interface web do Zabbix

---

## 8. Plano de Ação (80/20)

| Ação | Impacto | Facilidade | Prioridade |
|----|--------|-----------|-----------|
| Desativar FTP | Alto | Média | Alta |
| Restringir MySQL | Alto | Alta | Alta |
| Revisar SMB | Médio | Média | Média |
| Revisar Zabbix | Médio | Alta | Alta |

---

## 9. Conclusão

A rede analisada apresenta **boa segmentação**, porém com **diversos serviços acessíveis** que requerem revisão e mitigação de riscos.

Os próximos passos envolvem:
- Implementar as recomendações propostas
- Definir regras de acesso mais restritivas
- Realizar monitoramento contínuo

---

## 10. Anexos

- Saídas dos comandos (`nmap`, `ip a`)
- Prints de terminal
- Estrutura de diretórios:

```
recon-backup/
├── corp_net/
├── infra_net/
└── guest_net/
```

- Arquivo do diagrama: `projeto-final-kensei.xml`

---

## Observação

Este projeto possui **finalidade exclusivamente educacional**, realizado em ambiente controlado e autorizado.
