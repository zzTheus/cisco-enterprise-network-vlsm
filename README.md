# 🌐 Infraestrutura de Rede Corporativa com VLSM — Cisco Packet Tracer

Projeto prático de planejamento, segmentação e implementação de uma infraestrutura de rede corporativa utilizando **VLSM (Variable Length Subnet Mask)**, roteamento inter-redes e serviços essenciais no **Cisco Packet Tracer**.

---

## 📌 Topologia da Rede

![Topologia de Rede](<Infraestrutura + HTTP e DNS funcionando>)

A rede foi projetada para atender a diferentes setores de uma organização, garantindo isolamento, eficiência no uso de endereçamento IPv4 e conectividade com a infraestrutura interna.

---

## 📊 Plano de Endereçamento (VLSM)

Bloco base utilizado: `172.16.0.0/16`

| Sub-rede / Setor | Prefixo / CIDR | Máscara de Sub-rede | Gateway Padrão | IP Inicial Útil | IP Final Útil | IP de Broadcast |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Rede Sem Fio (Visitantes)** | `/23` | `255.255.254.0` | `172.16.0.1` | `172.16.0.1` | `172.16.1.254` | `172.16.1.255` |
| **Desenvolvimento** | `/24` | `255.255.255.0` | `172.16.2.1` | `172.16.2.1` | `172.16.2.254` | `172.16.2.255` |
| **Administrativo** | `/25` | `255.255.255.128` | `172.16.3.1` | `172.16.3.1` | `172.16.3.126` | `172.16.3.127` |
| **Data Center (Servidores)** | `/28` | `255.255.255.240` | `172.16.3.129` | `172.16.3.129` | `172.16.3.142` | `172.16.3.143` |

---

## ⚙️ Tecnologias e Serviços Implementados

* **Roteamento Inter-VLAN / Inter-Subredes:** Roteador central Cisco 2811 interligando os segmentos de rede via interfaces FastEthernet.
* **Serviço DHCP:** Distribuição dinâmica de IPs para os hosts locais e rede sem fio.
* **Serviço DNS:** Resolução de nomes interna para a intranet corporativa (`http://www.empresa.com`).
* **Serviço Web (HTTP):** Hospedagem de página corporativa acessível por todas as sub-redes.
* **Ponto de Acesso Sem Fio:** Roteador Wireless configurado para atender dispositivos móveis na rede de visitantes.

---

## 🧪 Validação e Testes

### 1. Tabela de Roteamento (Cisco IOS)
Verificação das rotas diretamente conectadas e do particionamento variável de sub-redes via CLI:

![Show IP Route](<Teste de Roteamento>)

### 2. Teste de Conectividade (ICMP & Resolução ARP)
Teste de conectividade inter-redes executado via terminal de host:

![Teste de Ping](<Teste de Conectividade Interna>)

> **Nota técnica:** A primeira perda de pacote (*Request timed out*) observada no comando `ping` é o comportamento padrão esperado do protocolo ARP (Address Resolution Protocol), que precisa resolver o endereço MAC do próximo salto antes de encapsular e encaminhar os pacotes ICMP seguintes.

---

## 📁 Arquivos do Projeto

* `Trabalho Cisco Packet Tracer.pkt` — Topologia configurada e pronta para simulação.
