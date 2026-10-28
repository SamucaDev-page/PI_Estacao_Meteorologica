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
Nossa metodologia de pesquisa visa organizar a investigação científica para resolver problemas práticos e teóricos do Desenvolvimento de um novo Sistema para a Estação Meteorológica da Fatec de Jau. 

Utilizamos a pesquisa qualitativa buscando entender significados, percepções, motivações e objetivos, trabalhando com dados não numéricos através de uma entrevista com o Cliente. 

Partiremos neste Semestre da Definição, formulando perguntas de pesquisa, com o preenchimento de Requisitos Funcionais e Requisitos Não Funcionais, objetivos e revisão bibliográfica da pagina atual, Planejamento / Desenho elaborando protocolo (métodos de coleta, amostra, ferramentas) e elaboração de uma página HTML estática coletando os dados do Sistema do fabricante do Radar e (rodar experimentos, aplicar surveys, extração de código, utilização) e análise estatística/qualitativa para realizar a Validação / Redação  através da Interpretação crítica dos resultados, discussão de limitações e escrita da Documentação da Aplicação WEB. 

Nossas investigações serão em Fontes Secundárias (Ambiente Acadêmico/Digital): Bases de dados científicas (IEEE Xplore, ACM Digital Library, Scopus, SciELO) para revisões e mapeamentos e Fontes Primárias (Ambiente Prático) como Repositórios de código abertos (GitHub, GitLab), Indústria, empresas de tecnologia ou startups parceiras, Ambientes controlados de laboratório universitário ou grupos de pesquisa.

# 2. Requisitos

## • Requisitos funcionais

### - RF 1 
**Exibir dados meteorológicos via iframe do Davis/WeatherLink**

O sistema deve incorporar um iframe da plataforma Davis/WeatherLink para exibir as informações meteorológicas disponibilizadas pela plataforma.

- URL do iframe fornecido pelo WeatherLink.
- Carregar o conteúdo incorporado da plataforma.
- Painel meteorológico exibido no sistema.

### - RF 2
**Coletar dados meteorológcos via API da FATEC**

O sistema deve integrar à API da FATEC para coletar dados meteorológicos periodicamente, sem necessidade de download manual e contínuo.

- Dados disponibilizados pela API da FATEC.
- Consultar a API e coletar os dados meteorológicos.
- Dados meteorológico disponíveis para a utilização do sistema.

### - RF 3
**Importar arquivos manualmente nos formatos CSV e XML**

O sistema deve permitir a importação manual de arquivos nos formatos CSV e XML para carregar dados.

- Arquivo CSV ou XML contendo dados meteorológicos.
- Validar o formato e a estrutura do arquivo, ler os registros e importar os dados.
- Dados meteorológicos armazenados no sistema e mensagem com o resultado da importação.
- Por solicitação do usuário.

### - RF 4  
**Filtrar e limpar automaticamente as colunas dos arquivos CSV**

O sistema deve descartar automaticamente, durante a importação de arquivos CSV, as colunas desnecessárias e armazenar apenas as variáveis meteorológicas previamente definidas para a estação.

- Identificar as colunas do arquivo, selecionar as variáveis predefinidas e desconsiderar as demais.
- Dados das variáveis selecionadas armazenadas no sistema
- Informar quando o arquivo não tem uma coluna obrigatória. 

### - RF 5  
**Consolidar e agregar dados meteorológicos por período** 

O sistema deve agrupar automaticamente os dados meteorológicos por dia, semana, mês e ano, calculando média, valores máximos e mínimos das variáveis aplicáveis e acumulados de precipitação, sem necessidade de criar planilhas manualmente.

- Dados meteorológicos armazenados no sistema, com data e horário das medições.
- Agrupar as medições por período e calcular as necessidades correspondentes a cada variável.
- Métricas diárias, semanais e anuias consolidadas.
- Automaticamente após a inclusão de novos dados.

### - RF 6  
**Exibir variáveis e indicadores meteorológicos**

O sistema deve exibir as variáveis e os indicadores meteorológicos da estação, incluindo:

*	**Precipitação:** Acumulado diário (mm), acumulado mensal (mm) e acumulado anual (mm).
*	**Umidade Relativa do Ar (%):** Média diária, valor máximo registrado (com respectivo horário) e valor mínimo registrado (com respectivo horário).
*	**Temperatura do Ar (°C):** Média diária, temperatura máxima (com respectivo horário) e temperatura mínima (com respectivo horário).
*	**Sensação Térmica (°C):** Máxima (índice de calor com respectivo horário) e mínima (resfriamento pelo vento com respectivo horário).
*	**Pressão Atmosférica (hPa):** Média, valor máximo e valor mínimo (corrigidos para o nível do mar).
*	**Vento:** Velocidade média (km/h), direção predominante (rosa dos ventos/pontos cardeais), velocidade máxima da rajada de vento (km/h com respectivo horário e direção da rajada).
*	**Extremos Anuais:** Registro histórico da temperatura máxima e mínima do ano corrente (com data e hora da ocorrência).

**Atributos:**

- Dados meteorológicos e métricas consolidadas disponíveis no sistema.
- Consultar e organizar as informações correspondentes a cada variável e período.
- Variáveis e indicadores meteorológicos apresentados na interface.
- Informar quando não houver dados disponíveis para determinada variável ou período 

### - RF 7 
**Exibir painel com visão geral das condições meteorológicas (dashboard)**

O sistema deve apresentar na página inicial as condições meteorológicas da última medição disponível, organizadas em cards ou tabelas, e gráficos interativos da evolução da temperatura, da pressão atmosférica em intervalos de 2 horas e velocidade do vento e suas rajadas

- Dados meteorológicos disponíveis no sistema, incluindo data e horário das medições.
- Consultar as últimas medições e organizar os dados para apresentação dos indicadores e gráficos.
- Painel com resumo das condições meteorológicas, data e horário da última medição e gráficos interativos.

### - RF 8 
**Gerar e visualizar gráficos meteorológicos sob demanda** 

O sistema deve permitir ao usuário selecionar uma grandeza meteorológica, como temperatura, umidade ou vento, e visualizar um gráfico dinâmico correspondente ao período escolhido: dia, semana, mês ou ano.

- Grandeza meteorológica e período selecionados pelo usuário.
- Consultar dados correspondentes à seleção e gerar o gráfico.
- Gráfico de grandeza selecionada, com identificação do período e da unidade selecionada.

### - RF 9 
**Disponibilizar e exportar boletins meteorológicos**

O sistema deve permitir a consulta e o download de boletins meteorológicos consolidados, contemplando:

- **Informativo Diário:** Apresentar os dados do dia em um modelo padronizado de relatório.
- **Informativo Mensal:** Apresentar o resumo do mês e o histórico pluviométrico organizado mês a mês.
- **Informativo Anual:** Apresentar o resumo consolidado dos dados do ano.
- **Exportação:** Disponibilizar os boletins nos formato PDF, XLSX (Excel) e CSV.

**Atribútos**

- Tipo de boletim, período de referência e formato de exportação selecionados pelo usuário.
- Consultar os dados consolidados do período e organizar o boletim para visualização ou exportação.
- Boletim disponível para consulta na interface ou download no formato escolhido.

### - RF 10
**Apresentar informações institucionais da estação meteorológica** 

O sistema deve disponibilizar uma sessão denominada "A Estação" para apresentar a história da estação meteorológica, os procedimentos técnicos de medição e a relação dos instrumentos meteorológicos em operação.

- Conteúdos institucionais, descrições dos procedimentos de medição e informações sobre instrumentos em operação.
- Organizar os conteúdos para consulta na sessão "A Estação"
- Páginas com a história da estação, os procedimentos técnicos e a lista de instrumentos meteorológicos. 

### - RF 11
**Exibir informações de contato e localização da estação**

O sistema deve disponibilizar uma sessão de contato e localização com mapa interativo, utilizando Google Maps ou OpenStreetMap, para indicar a posição da estação meteorológica. Apresentar latitude, longitude, altitude, endereço físico, telefone e e-mail institucional

- Carregar o mapa interativo, posicionar o marcador conforme a latitude e a longitude e organizar as informações de localização e contato.
- Mapa com a localização da estação, acompanhando as coordenadas, da altitude e dos dados de contato. 

### - RF 12 
**Solicitar séries históricas e dados meteorológicos específicos**

O sistema deve permitir que os usuários externos, como pesquisadores, seguradoras e estudantes, solicitem séries históricas ou dados de registros analógicos por meio de um formulário integrado ao sistema.

- Nome, e-mail, instituição ou vínculo, finalidade da solicitação, período de interesse e descrição dos dados desejados.
- Validar os campos obrigatórios e registrar a solicitação para análise dos responsáveis pela estação.
- Solicitação registrada e mensagem de confirmação ao usuário
- informar campos obrigatórios ausentes, dados inválidos ou falha no registro da solicitação, permitindo corrigir e tentar novamente.   

### - RF 13 
**Notificar a equipe responsável por e-mail sobre novas solicitações** 

O sistema deve enviar automaticamente para o e-mail da equipe responsável pela estação os dados preenchidos no formulário de solicitação de séries históricas ou dados meteorológicos específicos.

- Dados da solicitação registrada e endereço de e-mail da equipe responsável.
- Organizar os dados da solicitação em uma mensagem e enviá-la automaticamente à equipe.
- E-mail de notificação contendo informações da solicitação.

### - RF 14 
**Controlar o acesso às funcionalidades por perfil de usuário**

O sistema deve aplicar o controle de acesso baseado em papéis (RBAC), disponibilizando as funcionalidades conforme as permissões de cada perfil:

- **Público / Visitante:** Permitir acesso, sem autenticação, ao portal informativo, aos gráficos com as últimas medições disponíveis, aos boletins públicos e ao formulário de solicitação.
- **Pesquisador / Parceiro Cadastrado:** Permitir acesso autenticado para download de séries históricas brutas e consolidadas.
- **Administrador / Operador:** Permitir acesso autenticado para gerenciar usuários, importar arquivos CSV e XML, inserir dados de registro analógicos antigos e editar informações institucionais.

**Atributos**

- Identificação do usuário, perfil atribuído e funcionalidade solicitada.
- Verificar a autenticação, quando necessária, e validar as permissões do perfil antes de autorizar a operação.
- Acesso permitido ou negado conforme as permissões do usuário.

### - RF 15
**Permitir o cadastro simplificado de usuários** 

O sistema deve disponibilizar um formulário de cadastro para pesquisadores e parceiros, solicitando apenas os dados necessários à identificação e à criação da conta, sem exigir informações sem relação com o acesso ao sistema

- Nome, E-mail, Senha
- Validar os campos obrigatórios, verificar se o e-mail já está cadastrado e registrar a conta.
- Conta criada e a mensagem de confirmação de cadastro.

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
O Modelo de Negócios Canvas proposto para a modernização da Estação Meteorológica busca estruturar o valor entregue aos usuários, otimizar os processos de coleta de dados e garantir a sustentabilidade operacional do projeto. A proposta central de valor consiste em disponibilizar uma plataforma centralizada, automatizada e de fácil acesso para consulta e exportação de dados meteorológicos tratados, eliminando a dependência de processos manuais e planilhas descentralizadas.


### A Figura 1 apresenta o Modelo de Negócios da Estação Meteorológica

## Figura 1. Modelo de Negócio Canvas

![image alt](https://github.com/SamucaDev-page/PI_Estacao_Meteorologica/blob/main/Modelo%20de%20neg%C3%B3cios-PI%20Esta%C3%A7%C3%A3o%20Meteorol%C3%B3gica.png?raw=true)
# 9. Design
(Paleta de cor, Tipografia, Logo, Wireframes, Modelo de navegação)

# 10. Protótipo
(Gere um protótipo funcional na ferramenta que se sentir mais confortável (Figma, por exemplo) e apresente aqui, indicando o link).

# 11. Aplicação

# 12. Considerações finais

# 11. Referências

