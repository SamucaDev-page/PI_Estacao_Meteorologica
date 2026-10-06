<p align="left" style="font-size:28px;"><strong><em>Documentação do PI</em></strong></p>
<details>
  <summary><strong>📑 Sumário</strong></summary>

- [1. Introdução](#1-introdução)
  - [Objetivos](#-objetivos)
  - [Metodologia](#-metodologia)
- [2. Requisitos](#2-requisitos)
  - [Requisitos funcionais](#-requisitos-funcionais)
  - [Requisitos não funcionais](#-requisitos-não-funcionais)
- [3. Modelo de casos de uso](#3-modelo-de-casos-de-uso)
- [4. Modelo do banco de dados](#4-modelo-do-banco-de-dados)
- [5. Banco de dados](#5-banco-de-dados)
- [6. Diagrama de classes](#6-diagrama-de-classes)
- [7. Estudo de viabilidade](#7-estudo-de-viabilidade)
- [8. Regras de negócio (Modelo canvas)](#8-regras-de-negócio-modelo-canvas)
- [9. Design](#9-design)
- [10. Protótipo](#10-protótipo)
- [11. Aplicação](#11-aplicação)
- [12. Considerações finais](#12-considerações finais)
- [13. Referências](#13-referências)

</details>

Para cada semestre, do 1º ao 6º, iremos utilizar este template para documentar o PI - incrementalmente.

# 1. Introdução
(Contextualização, Justificativa (porquê?)

## • Objetivos

## • Metodologia
(Que métodos, tecnologias, modelos de processo, ferramentas irá utilizar?  
Responde à pergunta: Como? Com o que? Onde? Quando?)  

# 2. Requisitos

## • Requisitos funcionais
(Escreva os requisitos funcionais da aplicação (funcionalidades esperadas, necessidades que devem ser atendidas))

### 2.1.1	Grupo de RF 1 
**Coleta Automática via API/Chave:**
O sistema deve integrar-se com a fonte de alimentação de dados (plataforma Davis/nuvem) através de API/chave de autenticação para extrair medições periodicamente sem necessidade de download manual
contínuo.

### 2.1.2	Grupo de RF 2
**Importação Manual de Arquivo (.csv / .xml):**
Como mecanismo de contingência caso a automação/API falhe ou para carregar períodos específicos, o sistema deve permitir upload manual de arquivos.

### 2.1.3	Grupo de RF 3  
**Filtragem e Limpeza Automática de Colunas:**
Ao importar o .csv, o sistema deve descartar automaticamente as colunas desnecessárias e persistir apenas as variáveis úteis pré-definidas da estação.

### 2.1.4	Grupo de RF 4  
**Consolidação e Agregação Temporal:** 
O sistema deve calcular e consolidar automaticamente as métricas por período:
Agrupamento diário, semanal, mensal e anual.
Cálculo automático de médias, valores máximos/mínimos e acumulados de precipitação, eliminando a criação manual de planilhas.

### 2.1.5	Grupo de RF 5  
**Gestão de Parâmetros Climáticos:**
•	Precipitação: Acumulado diário (mm), acumulado mensal (mm) e acumulado anual (mm).
•	Umidade Relativa do Ar (%): Média diária, valor máximo registrado (com respectivo horário) e valor mínimo registrado (com respectivo horário).
•	Temperatura do Ar (°C): Média diária, temperatura máxima (com respectivo horário) e temperatura mínima (com respectivo horário).
•	Sensação Térmica (°C): Máxima (índice de calor com respectivo horário) e mínima (resfriamento pelo vento com respectivo horário).
•	Pressão Atmosférica (hPa): Média, valor máximo e valor mínimo (corrigidos para o nível do mar).
•	Vento: Velocidade média (km/h), direção predominante (rosa dos ventos/pontos cardeais), velocidade máxima da rajada de vento (km/h com respectivo horário e direção da rajada).
•	Extremos Anuais: Registro histórico da temperatura máxima e mínima do ano corrente (com data e hora da ocorrência).

### 2.1.6	Grupo de RF 6 
**Página Inicial (Dashboard / Visão Geral):**
Exibição das condições atuais (dados em tempo real / última medição disponível).
Apresentação resumida em cards ou tabelas limpas (inspirado no padrão de estações de referência como a da USP).
Gráficos interativos rápidos: evolução de temperatura, pressão atmosférica (intervalos de 2 em 2 horas) e rajadas/velocidade do vento.

### 2.1.7	Grupo de RF 7 
**Geração e Visualização de Gráficos Sob Demanda:** 
Permitir que o usuário clique em uma grandeza específica (ex.: temperatura, umidade, vento) e visualize um gráfico dinâmico por período selecionável (dia, semana, mês, ano).

### 2.1.8	Grupo de RF 8 
**Informativos e Boletins Meteorológicos:**
Disponibilização para consulta e download dos boletins consolidados:
Informativo Diário (layout padrão de relatório).
Informativo Mensal (resumo com histórico pluviométrico mês a mês).
Informativo Anual.
Opção de exportar relatórios nos formatos PDF, .xlsx (Excel) e .csv.

### 2.1.9	Grupo de RF 9
**Seção Institucional ("A Estação"):** 
Páginas dedicadas à apresentação da história da estação, procedimentos técnicos de medição e lista dos instrumentos meteorológicos em operação.

### 2.1.10	Grupo de RF 10
**Seção de Contato e Localização:**
Integração com mapa interativo (Google Maps/OpenStreetMap) indicando a localização exata da estação (coordenadas: Latitude, Longitude e Altitude).
Dados institucionais: endereço físico, telefone e e-mail de contato.

### 2.1.11	Grupo de RF 11 
**Solicitação de Dados Específicos / Pesquisa:**
Formulário integrado para usuários externos (pesquisadores, seguradoras, estudantes) solicitarem séries históricas ou dados analógicos específicos.

### 2.1.12	Grupo de RF 12 
**Notificação Automática por E-mail:** 
Envio automatizado dos dados preenchidos na solicitação diretamente para o e-mail da equipe responsável pela estação.

### 2.1.13	Grupo de RF 13 
**Perfis e Níveis de Acesso (RBAC):**
Público/Visitante: Acesso irrestrito ao portal informativo, gráficos em tempo real, boletins públicos e formulário de solicitação.
Pesquisador/Parceiro Cadastrado: Acesso autenticado com permissão para download de séries históricas brutas/consolidadas.
Administrador/Operador: Gestão de usuários, carga manual de arquivos (.csv/.xml), inserção de dados analógicos antigos e edição de parâmetros institucionais.

### 2.1.14	Grupo de RF 14
**Cadastro Simplificado:** 
Fluxo de cadastro sem burocracia ou exigência de campos desnecessários.


## • Requisitos não funcionais
(Escreva os requisitos não funcionais da aplicação (qualidade))  
- Requisitos de produto  
- Requisitos de organização  
- Requisitos de confiabilidade  
- Requisito de implementação  
- Requisito de padrões  
- Requisitos de interoperabilidade

### 2.2.1	Grupo de RNF 1 
**Usabilidade e Interface (UI/UX):** 
O layout deve ser moderno, limpo, responsivo e estruturado em tabelas e cards intuitivos, reduzindo redundâncias visuais.

### 2.2.2	Grupo de RNF 2
**Disponibilidade e Confiabilidade:** 
O sistema deve operar de forma ininterrupta (meta de 99.5% de disponibilidade) para garantir que consultas públicas e acadêmicas estejam sempre acessíveis.

### 2.2.3	Grupo de RNF 3
**Resiliência e Desacoplamento:** 
O sistema não deve depender criticamente de uma única interface externa; falhas temporárias na API da estação devem ser tratadas com logs de erro claros e chaveamento para o upload manual de contingência.

### 2.2.4	Grupo de RNF 4
**Segurança da Informação:**
Uso obrigatório de protocolo seguro HTTPS com certificado SSL.
Armazenamento de credenciais de acesso e chaves de API criptografadas.
Proteção contra ataques comuns na web (injeção de SQL, CSRF e XSS).

### 2.2.5	Grupo de RNF 5
**Desempenho:** 
Carregamento do painel inicial em menos de 2 segundos sob condições normais de rede, com cache de consultas históricas consolidadas.


# 3. Modelo de casos de uso

# 4. Modelo do banco de dados
(Modelo conceitual, Modelo lógico, Físico)

# 5. Banco de dados

# 6. Diagrama de classes

# 7. Estudo de viabilidade

# 8. Regras de negócio (Modelo canvas)

# 9. Design
(Paleta de cor, Tipografia, Logo, Wireframes, Modelo de navegação)

# 10. Protótipo
(Gere um protótipo funcional na ferramenta que se sentir mais confortável (Figma, por exemplo) e apresente aqui, indicando o link).

# 11. Aplicação

# 12. Considerações finais

# 11. Referências

