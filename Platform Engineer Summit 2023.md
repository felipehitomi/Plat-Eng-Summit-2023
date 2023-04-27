Dia 1 - https://www.youtube.com/watch?v=YmQTusKg7-8

Matheus Fidelis - Engenharia de Confiabilidade: Roadmap da Resiliência
https://youtu.be/YmQTusKg7-8?t=1154
@fidelissauro
linktr.ee/fidelissauro


**Resiliência em QA / DevOps**

Testes
Linters
Business Tests Contratos
Feature Toggles
Canary
Blue / Green
Rollback rápido?

**Resiliência em Segurança**

Monitoramento
Perimetro
DMZ
DDOS
WAF
Scans na Pipeline
SAST & DAST Continuos
Thread Inteligence

**Chaos Intencional**

Testar a resiliência dos clientes e Serviços
Plataforma / Cloud 
	Chaos Monkey
Kubernetes
	Chaos Mesh
	Gremlin
	LitmusChaos 
Development
	Hystrix*
	Resilience4j
	GoBreaker
	Chaos Monkey Libs

**PRR Review Production Checklist**

Healthcheck dos produtos e dependências
Garantir de verdade
MVP não é desculpa
Deu certo, e agora???
Revisitar periodicamente
Score de confiança interno 
Até quando é do controle do SRE?



**Templates & Golden Path**

Começar do zero com tudo que tem de melhor
Aprendizado continuo
Reaproveitamento Ganho de tempo
Templates
Tudo "By Default"
Como manter tudo isso sem inibir inovação?
Quais as melhores ferramentas?
Quais as melhores práticas? 
Quais as melhores recomendações?
Tudo isso já vem por default? 
Como garantir isso rápido? 
Como evoluir isso?



**O QUE É SRE?**

Site Reliability Engineering
Engenharia de Confiabilidade
Ben Treynor Sloos, Vice Presidente de Engenharia do Google
Incorporar aspectos de Engenharia em Operações
Garantir a Confiabilidade de Software e Produtos

![[2023-04-25_18-46.png]]

O'REILLY Site Reliability Engineering
O'REILLY The Site Reliability Workbook
O'REILLY Building Secure & Reliable Systems



Métricas de Confiabilidade

Acordos

SLA
Service Level Agreement
O número previsto em contrato. 
A obrigação.
Nunca pode ser 100%.

SLO
Service Level Objective
O objetivo de melhora da métrica.
Mais rigoroso que o SLA 
A estrela guia.
Nunca pode ser 100%.

SLI
Service Level Indicator
O indicador de performance do SLO e SLA
O dedo duro.

Error Budget
O quanto falta pro SLO & SLA serem quebrados?
A margem de erro.



Métricas RED
Métricas voltadas para serviços e microsserviços
Modelo baseado em uso de serviço


Rate
Número de Requests em um determinado range de tempo
Error
Porcentagem de erros em um determinado range de tempo
Duration
Duração média, maxima, p99, p90, p50 dos requests dentro de um determinado range de tempo

![[2023-04-25_18-47.png]]

Nassim Nicholas Taleb
THE BLACK SWAN
Antifragile


Lidando seus Cisnes
Conversando e Conhecendo
Mapeamento visual
Game Days
Simulações de Desastres 
Perguntas Cretinas
Assumindo Riscos como Produto
Post-Mortens


BLAST RADIUS
Estimar e diminuir os impactos
Termo Utilizado pelos times da AWS
Zona de Impacto de um desastre
Qual o dano?
Quais os Workloads Afetados?
Quais as dependências
O que está em Outage
O que será degradado parcialmente?
O que ainda funciona?


Como Medir?
	Matriz de Resiliência
	Healthmaps
	Game Days
	Simulações de Desastre
	"Perguntas Cretinas"
		"O que acontece quando isso aqui cair?" - Pergunta Cretina
		"Se eu desligar isso aqui, esse outro ainda funciona?" - Pergunta Cretina
		"O que podemos fazer pra isso aí não cair junto? Ou quem sabe minimizar o impacto da queda?" - Pergunta Cretina

Disaster Recovery
Um desastre, é um desastre por definição 
Quem define o que é um desastre?

Capacidade de escolher entre
	Tomar uma voadora
	Tomar um soco
	Tomar um tapa

Minimizar e contornar os impactos 
Simular é melhor que o acaso
Medir o Blast Radius
Gerar Backlog


Disaster Recovery & Game Days
Objetivos
Backlog das Perguntas Cretinas
Simular o impacto real delas
Diminuir as Dependências
Criar fluxos alternativos
TradeOffs
Testar ativamente os fluxos alternativos
Desligar dependências, simular falhas e manter os SLO's


Resiliência de Infraestrutura
Redundancia de Networking
Multi-AZ & Multi Region 
Backups, Snapshots, Restore 
Recursos Redundantes
Camadas de Dados
Região e Plano de DR?
Capacity Planning
Plataforma
SLA dos fornecedores

Resiliência de Sistêmica
Programação Defensiva
Healthchecks
Sync e Async
Retry Policies
Circuit Breakers
Fault Injection 
Fallbacks
Desacoplamento e Isolamento
Camadas de Dados


Retry Policies
Primeiro Passo
Integrações Pragmáticas
Retentativa de Comunicação Sync
Priorizar comunicação Async
Sempre pensar num fallback
Mensageria e Filas Async
Plataforma Inbound & Outbound 
Timeout nas Integrações


Fallbacks
Sempre pensar em fluxos alternativos 
Duvida entre duas ou mais soluções?
	Use várias
Duvida entre dois ou mais parceiros?
	Tenha vários
Fluxo reserva
Mensageria, Reservas, Fluxo
Represagem
Processamento tardio

Circuit Breakers
Dar erro mais rápido?
Uso inteligente dos Fallbacks
Trabalhar com as falhas de forma prevista
Thresholds 5xx, conn, business
Fallback acionado de forma inteligente
Quebra tornar o fallback prioritário
Checagem inteligente
Monitoramento


Fault Injection
Injetar erros primários internacionais 
Testar ativamente os fallbacks
Problemas de monitoramento 
Porcentagens aceitáveis do fluxo principal
Chaos Engineering - Assaults
	Latency Injection
	Error Injection
	App Killer
	Memory & CPU
	Container exit