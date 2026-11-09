# gerenciando-maquinas-virtuais-no-azure
Documentação técnica, anotações e boas práticas sobre implantação, alta disponibilidade e gerenciamento de Máquinas Virtuais no Microsoft Azure (Desafio DIO).

# ☁️ Gerenciando Máquinas Virtuais no Microsoft Azure

Este repositório foi desenvolvido como parte de um desafio prático da plataforma DIO, com o objetivo de consolidar e documentar os conhecimentos adquiridos sobre a administração e o gerenciamento de infraestrutura como serviço (IaaS) no Microsoft Azure.

---

## 📌 Sumário
- [Visão Geral](#-visão-geral)
- [Principais Conceitos Estudados](#-principais-conceitos-estudados)
  - [1. Implantação e Tipos de Discos](#1-implantação-e-tipos-de-discos)
  - [2. Alta Disponibilidade e Redundância](#2-alta-disponibilidade-e-redundância)
  - [3. Dimensionamento (Scaling)](#3-dimensionamento-scaling)
  - [4. Segurança e Acesso Remoto](#4-segurança-e-acesso-remoto)
- [Boas Práticas e Recomendações](#-boas-práticas-e-recomendações)
- [Recursos Úteis](#-recursos-úteis)

---

## 🔍 Visão Geral
O foco deste laboratório é entender o ciclo de vida e a arquitetura das Máquinas Virtuais (VMs) no Azure, identificando os modelos recomendados para ambientes de produção, estratégias para minimizar o tempo de inatividade e técnicas de autoescalonamento.

---

## 🧠 Principais Conceitos Estudados

### 1. Implantação e Tipos de Discos
- **Ambientes de Produção:** Devem utilizar discos de alta performance (SSD Standard/Premium) e possuir rotinas de backup ativas.
- **Modelos Spot:** O uso de instâncias Spot não é recomendado para ambientes de produção devido ao risco de desalocação (*eviction*) imprevista por parte da Microsoft.
- **Gerenciamento de Discos:** Capacidade de anexar, desanexar e redimensionar discos de dados sem impactar a execução da VM.

### 2. Alta Disponibilidade e Redundância
- **Conjuntos de Disponibilidade (Availability Sets):** Agrupamento lógico que distribui as VMs em diferentes hardware físicos dentro de um mesmo data center para garantir redundância.
- **Domínios de Falha (Fault Domains):** Máquinas que compartilham a mesma fonte de energia e switch de rede (racks distintos).
- **Domínios de Atualização (Update Domains):** Grupos de VMs que são reiniciados separadamente durante manutenções planejadas do Azure.

### 3. Dimensionamento (Scaling)
- **Escalonamento Vertical (*Scale Up/Down*):** Alteração no tamanho ou especificações (CPU/RAM) de uma única VM.
- **Escalonamento Horizontal (*Scale Out/In*):** Adição ou remoção de instâncias de VMs para distribuir a carga.
- **Virtual Machine Scale Sets (VMSS):** Gerenciamento automatizado de grupos de VMs idênticas com regras de dimensionamento baseadas em métricas (ex: ajustar instâncias quando a CPU ultrapassa 85% ou cai abaixo de 15%).

### 4. Segurança e Acesso Remoto
- **Autenticação Segura:** Uso prévio de chaves SSH protegidas por passphrase.
- **Azure Bastion:** Conectividade RDP/SSH totalmente gerenciada via portal (navegador) sem expor IPs públicos à internet.
- **Modelo de Responsabilidade Compartilhada:** O Azure responde pela infraestrutura física, enquanto o cliente gerencia o SO, aplicativos e backups.

---

## 💡 Boas Práticas e Recomendações
1. **Redundância:** Sempre utilize conjuntos de disponibilidade + balanceadores de carga para serviços críticos.
2. **Automação:** Adote regras baseadas em métricas para otimizar custos e desempenho sem necessidade de intervenção manual.
3. **Segurança:** Evite portas RDP/SSH abertas para a internet pública; prefira Azure Bastion ou VPN.

---

## 🔗 Recursos Úteis
- [Documentação Oficial do Microsoft Azure](https://learn.microsoft.com/pt-br/azure/)
- [Gerenciar Máquinas Virtuais no Azure](https://learn.microsoft.com/pt-br/azure/virtual-machines/)
