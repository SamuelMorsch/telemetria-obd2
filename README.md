# 🚗 Sistema de Telemetria Automotiva Remota

![Status](https://img.shields.io/badge/Status-Em%20Desenvolvimento-orange)
![Flutter](https://img.shields.io/badge/Mobile-Flutter-blue)
![Node.js](https://img.shields.io/badge/Backend-Node.js-green)
![React](https://img.shields.io/badge/Frontend-React/Next.js-blueviolet)

## 📖 Visão Geral
Este repositório documenta a proposta e a arquitetura do **Sistema de Telemetria Automotiva Remota**, um projeto de Engenharia de Software focado no diagnóstico de falhas elétricas intermitentes em veículos automotores. 

O projeto visa solucionar o gargalo de diagnósticos estáticos em oficinas mecânicas, permitindo que especialistas monitorem as quedas de voltagem do alternador e da bateria em tempo real, enquanto o veículo está em circulação normal nas vias.

## Problema e Necessidade de Mercado
* **O Problema:** Falhas intermitentes raramente se manifestam com o carro parado na oficina, resultando em diagnósticos inconclusivos e testes de bancada frustrantes.
* **A Necessidade:** O mercado carece de uma ferramenta focada no profissional técnico (mecânico/autoelétrica) que permita visualizar o micro-comportamento elétrico do motor à distância, preenchendo a lacuna deixada por aplicativos de autoatendimento para motoristas leigos e plataformas corporativas de gestão logística.

## Inovação
A inovação central do projeto reside na transição do foco comercial B2C para o modelo de ferramenta "oficina-veículo". Atuando como um "multímetro virtual remoto", a solução terceiriza a conectividade de rede para o smartphone do próprio condutor (reduzindo custos de hardware) e transmite as séries temporais diretamente para o laboratório de análise da oficina.

## Arquitetura e Tecnologias
O ecossistema é baseado em um modelo cliente-servidor descentralizado, operando em três frentes principais:

1. **Camada de Borda (Mobile Gateway) - `Flutter`**
   * Comunicação Bluetooth Low Energy (BLE) com o scanner OBD-II físico (chip ELM327).
   * Extração, conversão e empacotamento cíclico dos parâmetros elétricos.
   * Transmissão de pacotes JSON temporais via HTTPS/Rede Celular (4G/5G).

2. **Camada Lógica (Backend API) - `Node.js`**
   * API RESTful construída para alta disponibilidade e suporte a processos assíncronos (non-blocking I/O).
   * Recepção de alto volume de dados (séries temporais) sem bloqueio de processos.
   * Validação, tratamento de perdas de pacote e persistência em banco de dados.

3. **Camada de Apresentação (Frontend Web) - `React / Next.js`**
   * Dashboard exclusivo para a oficina mecânica.
   * Renderização de gráficos dinâmicos de linhas que reagem em tempo real às atualizações da API.

## Próximos Passos (Cronograma)
- [ ] Implementação da conexão BLE nativa.
- [ ] Estruturação dos *endpoints* da API Node.js para recebimento de JSON.
- [ ] Implementação de rotinas de armazenamento local (*offline-first*) para áreas de sombra de cobertura celular.
- [ ] Construção dos componentes de plotagem gráfica no React.
