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
As estações meteorológicas são responsáveis pela coleta e registro de dados climáticos importantes, como temperatura, umidade relativa do ar, precipitação, pressão atmosférica e velocidade e direção dos ventos. Esses dados possuem relevância para pesquisas acadêmicas, acompanhamento das condições meteorológicas e consulta de séries históricas.

Atualmente, parte do processo de obtenção, organização e consolidação dos dados da estação meteorológica é realizada de forma manual contendo vários retrabalhos, envolvendo arquivos e planilhas que precisam ser tratados para a geração de informações diárias, mensais e anuais. Esse processo pode demandar tempo, dificultar a consulta aos registros históricos e aumentar a possibilidade de inconsistências durante a manipulação dos dados.

Diante desse cenário, o projeto propõe o desenvolvimento de uma plataforma web para centralização, processamento e disponibilização dos dados da estação meteorológica. O sistema realizará a coleta automática de medições por meio de integração com API, além de permitir a importação manual de arquivos como mecanismo de contingência. Os dados serão tratados, armazenados e utilizados para geração de indicadores, gráficos, boletins e séries históricas. Também haverá um dashboard com graficos sendo atualizados em tempo real contendo informações meteorológicas importantes

A justificativa do projeto está, portanto, na necessidade de reduzir atividades manuais, centralizar o acervo meteorológico, facilitar o acesso às informações e proporcionar maior eficiência na organização, análise e disponibilização dos dados da estação.

## • Objetivos
Automatizar a ingestão, o tratamento, o armazenamento e a visualização de dados climáticos, eliminando etapas manuais de filtragem de arquivos .csv, redigitação em planilhas e consolidações manuais (semanais, mensais e anuais). 

## • Metodologia
(Que métodos, tecnologias, modelos de processo, ferramentas irá utilizar?  
Responde à pergunta: Como? Com o que? Onde? Quando?)  

# 2. Requisitos

## • Requisitos funcionais

### - RF 1 
**Coleta Automática via API/Chave:**

O sistema deve integrar-se com a fonte de alimentação de dados (plataforma Davis/nuvem) através de API/chave de autenticação para extrair medições periodicamente sem necessidade de download manual
contínuo.

### - RF 2
**Importação Manual de Arquivo (.csv / .xml):**

Como mecanismo de contingência caso a automação/API falhe ou para carregar períodos específicos, o sistema deve permitir upload manual de arquivos.

### - RF 3  
**Filtragem e Limpeza Automática de Colunas:**

Ao importar o .csv, o sistema deve descartar automaticamente as colunas desnecessárias e persistir apenas as variáveis úteis pré-definidas da estação.

### - RF 4  
**Consolidação e Agregação Temporal:** 

O sistema deve calcular e consolidar automaticamente as métricas por período:
Agrupamento diário, semanal, mensal e anual.
Cálculo automático de médias, valores máximos/mínimos e acumulados de precipitação, eliminando a criação manual de planilhas.

### - RF 5  
**Gestão de Parâmetros Climáticos:**

*	Precipitação: Acumulado diário (mm), acumulado mensal (mm) e acumulado anual (mm).
*	Umidade Relativa do Ar (%): Média diária, valor máximo registrado (com respectivo horário) e valor mínimo registrado (com respectivo horário).
*	Temperatura do Ar (°C): Média diária, temperatura máxima (com respectivo horário) e temperatura mínima (com respectivo horário).
*	Sensação Térmica (°C): Máxima (índice de calor com respectivo horário) e mínima (resfriamento pelo vento com respectivo horário).
*	Pressão Atmosférica (hPa): Média, valor máximo e valor mínimo (corrigidos para o nível do mar).
*	Vento: Velocidade média (km/h), direção predominante (rosa dos ventos/pontos cardeais), velocidade máxima da rajada de vento (km/h com respectivo horário e direção da rajada).
*	Extremos Anuais: Registro histórico da temperatura máxima e mínima do ano corrente (com data e hora da ocorrência).

### - RF 6 
**Página Inicial (Dashboard / Visão Geral):**

Exibição das condições atuais (dados em tempo real / última medição disponível).
Apresentação resumida em cards ou tabelas limpas (inspirado no padrão de estações de referência como a da USP).
Gráficos interativos rápidos: evolução de temperatura, pressão atmosférica (intervalos de 2 em 2 horas) e rajadas/velocidade do vento.

### - RF 7 
**Geração e Visualização de Gráficos Sob Demanda:** 

Permitir que o usuário clique em uma grandeza específica (ex.: temperatura, umidade, vento) e visualize um gráfico dinâmico por período selecionável (dia, semana, mês, ano).

### - RF 8 
**Informativos e Boletins Meteorológicos:**

Disponibilização para consulta e download dos boletins consolidados:
Informativo Diário (layout padrão de relatório).
Informativo Mensal (resumo com histórico pluviométrico mês a mês).
Informativo Anual.
Opção de exportar relatórios nos formatos PDF, .xlsx (Excel) e .csv.

### - RF 9
**Seção Institucional ("A Estação"):** 

Páginas dedicadas à apresentação da história da estação, procedimentos técnicos de medição e lista dos instrumentos meteorológicos em operação.

### - RF 10
**Seção de Contato e Localização:**

Integração com mapa interativo (Google Maps/OpenStreetMap) indicando a localização exata da estação (coordenadas: Latitude, Longitude e Altitude).
Dados institucionais: endereço físico, telefone e e-mail de contato.

### - RF 11 
**Solicitação de Dados Específicos / Pesquisa:**

Formulário integrado para usuários externos (pesquisadores, seguradoras, estudantes) solicitarem séries históricas ou dados analógicos específicos.

### - RF 12 
**Notificação Automática por E-mail:** 

Envio automatizado dos dados preenchidos na solicitação diretamente para o e-mail da equipe responsável pela estação.

### - RF 13 
**Perfis e Níveis de Acesso (RBAC):**

Público/Visitante: Acesso irrestrito ao portal informativo, gráficos em tempo real, boletins públicos e formulário de solicitação.
Pesquisador/Parceiro Cadastrado: Acesso autenticado com permissão para download de séries históricas brutas/consolidadas.
Administrador/Operador: Gestão de usuários, carga manual de arquivos (.csv/.xml), inserção de dados analógicos antigos e edição de parâmetros institucionais.

### - RF 14
**Cadastro Simplificado:** 

Fluxo de cadastro sem burocracia ou exigência de campos desnecessários.


## • Requisitos não funcionais

### - RNF 1 
**Usabilidade e Interface (UI/UX):** 

O layout deve ser moderno, limpo, responsivo e estruturado em tabelas e cards intuitivos, reduzindo redundâncias visuais.

### - RNF 2
**Disponibilidade e Confiabilidade:** 

O sistema deve operar de forma ininterrupta (meta de 99.5% de disponibilidade) para garantir que consultas públicas e acadêmicas estejam sempre acessíveis.

### - RNF 3
**Resiliência e Desacoplamento:** 

O sistema não deve depender criticamente de uma única interface externa; falhas temporárias na API da estação devem ser tratadas com logs de erro claros e chaveamento para o upload manual de contingência.

### - RNF 4
**Segurança da Informação:**

Uso obrigatório de protocolo seguro HTTPS com certificado SSL.
Armazenamento de credenciais de acesso e chaves de API criptografadas.
Proteção contra ataques comuns na web (injeção de SQL, CSRF e XSS).

### - RNF 5
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

