![Capa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Seu IoT 1.1: seus dados em qualquer tela, e conectados ao resto do mundo

**Uma nova central de visualização de dados, tabelas e mapas que cruzam projetos, status online/offline de cada dispositivo, API aberta com widgets para colar no seu site e conexão com assistentes de IA. Tudo sob o seu controle.**

**Versão:** Plataforma 1.1.0 | Firmware 2.0.1 | **Data:** 2026-10-13

---

A versão 1.0 anterior trouxe o Blueprint e a forma de **montar** o funcionamento do seu sistema. A **1.1** trata do que vem depois: **enxergar o que o sistema está produzindo** e **levar esses dados para onde você precisar**.

Foram três frentes de trabalho:

1. **Visualização de dados:** novos tipos de gráfico, indicadores (KPIs), medidores, tabelas e mapas, e uma tela de criação de gráficos totalmente redesenhada.
2. **Estado de conexão dos dispositivos:** agora a plataforma registra quando cada dispositivo ficou online e offline, e isso vira dado para gráficos.
3. **Integrações:** uma API aberta para sistemas de terceiros, widgets que você cola em qualquer página e o acesso de assistentes de IA (Claude, Cursor, Gemini CLI e outros) via MCP.

Junto com a plataforma, o **firmware 2.0.1** corrige a edição de processos direto no dispositivo e permite encadear uma leitura I2C numa escrita I2C.

![Visão geral de um painel com os novos tipos de gráfico lado a lado](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/dashboard_overview.gif)

---

## Uma nova tela para criar gráficos

Antes de falar dos gráficos em si, a mudança que os sustenta: a criação de gráficos ganhou uma **tela própria**, com a escolha do tipo (**Gráfico linear, Composição, Indicador, Medidor, Recipiente, Mapa de calor, Tabela e Mapa**) e uma **pré-visualização ao vivo** durante a configuração. É a mesma tela, com as mesmas opções, tanto dentro de um **projeto (Blueprint)** quanto no **painel**.

![Escolha do tipo de gráfico com a pré-visualização ao vivo](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/chart_creator_catalog.gif)

**Por que importa:** no painel, um gráfico pode agora reunir **sinais de vários projetos e dispositivos** no mesmo lugar. Antes, cada gráfico de painel ficava preso a uma única origem. Um painel de operação já não precisa de um gráfico por projeto: ele pode comparar o que está acontecendo em todos.

O painel também ganhou o modo **Tela cheia**, pensado para ficar aberto numa TV ou num monitor de sala de controle.

![Painel em tela cheia](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/dashboard_fullscreen.png)

---

## Novos tipos de gráfico

### Indicadores (KPIs): do último valor a estatísticas de verdade

O **Indicador** de **Último valor** agora mostra a **unidade de medida** (ex.: "23,5 °C"), e ganhou companhia: são **14 tipos de indicador (KPI)**, organizados em grupos (Leitura, Tendência e comparação, Estatística de período, Faixa normal, Frota e acumulados), cada um com uma explicação e um exemplo no catálogo de tipos.

![Catálogo de tipos de indicador, com exemplo de cada um](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/kpi_type_catalog.gif)

| Tipo de indicador | O que mostra |
|---|---|
| Último valor | A última leitura recebida |
| Estatística de período | Média, mínimo, máximo ou contagem de leituras no período do card |
| Comparação com meta/alvo | A última leitura frente a um valor-alvo que você define |
| Seta de tendência simples | Se o valor está subindo ou descendo |
| Com tempo da última leitura | A leitura com "há 3 min" ao lado |
| % de amostras dentro da faixa normal | Quanto do período ficou dentro do esperado |
| Comparação com período anterior | O período atual frente ao anterior (hora, dia, semana, mês ou ano) |
| Percentil (p90/p95) | O valor que ignora picos raros |
| Desvio padrão/variabilidade | O quanto a leitura oscila |
| Contagem de violações de faixa | Quantas vezes o valor saiu da faixa normal |
| Contagem de ciclos/execuções | Quantas vezes o processo publicou uma leitura |
| Projeção simples (extrapolação linear) | Extrapola a tendência e estima quando o limite será atingido |
| Ranking dentro da frota | A posição do dispositivo frente aos demais do projeto |
| Consumo acumulado calculado | Soma acumulada ao longo do tempo (ex.: kWh) |

Você escolhe o que mostrar junto com o valor: hora, dispositivo, local, processo, operador e cliente.

> **Exemplo:** o indicador "% de amostras dentro da faixa normal" de um freezer de laboratório mostra "92% dentro da faixa (7 dias)". Num relance você sabe se o equipamento está se comportando, sem abrir gráfico nenhum.

### Medidor e recipiente: ver o nível, não só o número

Dois novos jeitos de mostrar **um valor dentro de uma escala** (mínimo e máximo), com **faixas de cor** que mudam conforme o valor cruza cada limite:

- **Medidor:** nos estilos **Velocímetro, Anel completo, Meio anel e Quarto de anel**.
- **Recipiente:** o nível enche de verdade, em nove formatos: **Tanque, Silo, Tanque deitado, Caixa aberta, Silo cônico, Botijão de gás, Barril, Barra de carregamento e Bateria**.

A cor pode ser em **blocos** (muda ao cruzar cada limite) ou em **degradê contínuo** entre as faixas.

![Medidor e recipiente com faixas de cor, mudando de cor ao cruzar os limites](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/gauge_and_container.gif)

![Galeria dos formatos de recipiente](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/container_shapes.gif)

> **Exemplo:** o nível de um reservatório como Tanque, verde acima de 40%, amarelo entre 20% e 40%, vermelho abaixo de 20%. Quem passa pela tela entende o estado sem ler nenhum número.

### Mapa de calor (calendário)

Um **valor por dia** pintado num calendário, ao estilo das contribuições do GitHub. Escolha a **agregação** (**Média, Soma, Contagem, Máximo ou Mínimo**) e o **período do calendário** (**Mês ou Ano**). Dias mais intensos ficam mais escuros, e o balão mostra a data, o valor e quantas amostras entraram no dia. Há botões para ir ao período anterior, ao próximo e voltar para hoje.

![Mapa de calor alternando entre Média e Contagem](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/calendar_heatmap.gif)

**Por que importa:** padrões que passam despercebidos num gráfico de linha de meses (como "toda segunda-feira o consumo dispara") ficam óbvios num calendário.

### Histograma

Entre os estilos do tipo **Composição** (Pizza, Mapa de árvore, Barra horizontal e Histograma), o **Histograma** mostra a **distribuição** dos valores de um processo num período: quantas leituras caíram em cada faixa. O **Número de baldes** pode ser **Automático (regra de Sturges)** ou fixo, e há degradê do primeiro ao último balde. Mudar o período recalcula tudo.

![Estilos do tipo Composição](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/composition_types.gif)

![Histograma mudando o número de baldes e o período](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/histogram.gif)

### Linha e área coloridas por faixa de valor

O traço do gráfico de linha ou de área **muda de cor** conforme o valor cruza as faixas que você definiu (verde, amarelo, vermelho), em blocos ou em degradê. Basta olhar para a linha para saber quando e por quanto o valor saiu do esperado.

![Gráfico de linha mudando de cor ao cruzar as faixas configuradas](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/colored_line_by_band.gif)

### Linhas de referência

Anotações fixas sobre o gráfico, independentes dos dados: uma linha **horizontal** (um limite de operação), **vertical** (um horário de corte) ou **inclinada**, entre dois pontos. Cada uma tem **rótulo, cor e estilo** (contínua, tracejada, pontilhada ou traço-ponto).

![Linhas de referência horizontal, num gráfico](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/reference_lines.gif)

### Ajustes nos gráficos existentes

- **Gráfico de barras:** a largura da barra agora se adapta a cards estreitos e a muitos pontos, sem vazar para fora do gráfico, e a primeira e a última barra não ficam mais cortadas nas bordas.
- **Gráficos de calibração:** agora mostram os últimos **15 pontos** em vez de 80, o que acabou com o "mar de pontos" ilegível. Arrastar para selecionar e calcular a média continua funcionando mesmo se o mouse sair da área do gráfico. A leitura em foco na lista é destacada no gráfico de regressão, e os valores nunca aparecem em notação científica.
- **Balões de informação e eixos** com cores mais legíveis nos temas claro e escuro, e o eixo Y se ajusta à largura real dos números.

---

## Tabelas e mapas que cruzam projetos

Esta é a mudança que mais amplia o que o painel consegue fazer. Até aqui, um gráfico ou widget de dados apontava para **um** projeto. Agora você define uma **regra de dispositivos** (com o botão **Adicionar regra**) e a plataforma resolve, a cada carregamento, quais dispositivos entram, sejam de que projeto forem.

A regra pode filtrar por:

- **Projeto** e **repositório**
- **Personna** (operador e cliente)
- **Modelos** (ex.: só ESP32-S3)
- **Somente online:** dispositivos com leitura nas últimas 24 horas
- **Área geográfica:** um círculo no mapa, com centro e **Raio (km)** que você arrasta

### Tabela configurável

Uma linha por dispositivo, e **você escolhe as colunas** (**Adicionar coluna**). A primeira é sempre o dispositivo; as outras podem ser de cinco tipos:

- **Identidade:** IP local, IP público, Projeto, Status, Modelo, Operador, Cliente e Localização.
- **KPI:** qualquer um dos 14 tipos de indicador, calculado para cada dispositivo.
- **Medidor:** o medidor dentro da célula.
- **Gráfico:** a tendência recente em um mini gráfico sem eixos.
- **Ação:** um botão, interruptor, controle deslizante ou campo de texto que **executa o processo naquele dispositivo**, direto da linha da tabela. O botão de uma leitura é o **Ler agora**.

![Tabela de dispositivos com colunas de identidade, KPI, medidor, gráfico e ação](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/table_widget.gif)

Ao clicar no operador, no cliente ou na localização de uma linha, um balão mostra os **dados de contato**, com atalhos para copiar, enviar e-mail, abrir o WhatsApp ou abrir no Google Maps.

> **Exemplo:** uma tabela "Câmaras frias" reunindo todos os dispositivos do cliente X em 5 projetos diferentes: status online, temperatura atual com medidor, tendência das últimas horas e um botão para forçar uma nova leitura. Tudo numa tela, sem entrar em projeto nenhum.

### Mapa com valores nos marcadores

O **Mapa** usa a mesma regra de dispositivos. Cada alfinete mostra **dados informativos** que você configura (indicadores, medidores e gráficos). **A cor do alfinete vem do dado informativo principal**, que precisa ser um medidor e é marcado com a estrela (por exemplo, vermelho nos dispositivos acima do limite de temperatura), e o balão mostra os demais dados ao clicar no dispositivo. Acima de cada alfinete você ainda pode alternar o nome do dispositivo, o operador, o cliente e a hora.

![Mapa de dispositivos com alfinetes coloridos pelo dado principal e balão com os dados informativos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/geo_map_values.gif)

Tabela e mapa também funcionam **dentro do Blueprint** de um projeto, agora como mais um tipo de card. O mapa passou a usar o **OpenStreetMap**, sem depender de um provedor de tiles que passou a exigir chave de API.

---

## Online e offline: o histórico de conexão de cada dispositivo

Até aqui a plataforma sabia **se** um dispositivo estava online. Agora ela também sabe **quando** ele conectou e desconectou. O broker MQTT passou a avisar cada evento, e o Seu IoT guarda o histórico.

O status é atualizado **em tempo real** nas listas de dispositivos e nos modais, sem precisar recarregar a página.

![Lista de dispositivos com o status online/offline mudando em tempo real](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/device_live_status.gif)

E o mais importante: a conectividade vira um **sinal como qualquer outro** nos seus gráficos, tabelas e mapas, no grupo **Conectividade** ao escolher o sinal. Existem quatro variações:

| Sinal | O que mostra |
|---|---|
| Estado da conexão | 1 quando conectado, 0 quando desconectado, um ponto por evento |
| Nº de desconexões | Quantas vezes o dispositivo caiu |
| Tempo conectado | Segundos acumulados online |
| Tempo desconectado | Segundos acumulados offline |

![Gráfico de estado de conexão de um dispositivo ao longo do dia](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/connection_state_chart.gif)

**Por que importa:** responder "esse sensor está caindo muito?" passa a ser uma questão de ler um gráfico ou uma coluna de tabela (a contagem de desconexões da semana, ou o percentual de tempo online), e não de investigar logs.

---

## Armazenamento: lixeira por projeto

A **lixeira** agora vale também para os dados dos **projetos**. Você pode mover os dados de um dispositivo de um projeto para a lixeira, restaurar, ou apagar de vez, e a regra de limpeza automática do seu plano passa a cuidar tanto dos dados de repositórios quanto dos de projetos. Os eventos de conexão também entram nessa limpeza.

O cartão de uso de armazenamento mostra o consumo **somando repositórios e projetos**, e o que está na lixeira deixa de aparecer nos gráficos, nas leituras ao vivo e na "última mensagem" do dispositivo.


---

## Publicação automática dos processos

Para um processo aparecer em gráficos, ele precisa **publicar** o resultado a cada execução. Agora isso está ao alcance de um clique:

- Um **ícone de envelope** no card do processo liga e desliga a **Publicação automática** (o ícone avisa "clique para desativar" ou "clique para ativar").
- Nas **configurações do projeto**, a opção **Publicação automática por padrão** define se **novos processos já nascem publicando** (por padrão, sim). Os processos criados passam realmente a herdar esse padrão.
- O botão que alterna entre o valor e o mini gráfico fica **desabilitado, com uma explicação**, quando o processo ainda não tem nenhum dado para plotar.

![Ícone de envelope no card do processo e a opção Publicação automática por padrão nas configurações do projeto](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/publish_on_execute.gif)

---

## API aberta: seus dados em sistemas de terceiros

Seus dados agora podem ser lidos por **sistemas que não têm conta no Seu IoT**, sem expor seu login e sem abrir o projeto inteiro.

Isso é feito por **Contratos de API**, criados nas configurações do projeto. Um contrato é uma **visão limitada** do projeto: você escolhe **quais processos** (e, se quiser, quais dispositivos) ele pode enxergar. Cada contrato entrega:

- **Chave HTTPS:** para consultar histórico e o valor atual.
- **Credencial MQTT/WS (tempo real):** para receber os valores **em tempo real**, assim que o dispositivo publica, sem precisar ficar perguntando.
- **Widgets incorporáveis** (veja a seguir).

![Criação de um contrato de API escolhendo processos e dispositivos do escopo](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_contract_creation.gif)

**Segurança e controle:**

- Você pode **revogar, reativar, regenerar as credenciais, definir quando o contrato expira e editar o escopo** a qualquer momento.
- A chave e a senha são mostradas **uma vez**, no momento em que são geradas.

**Acompanhamento de uso:** a lista de contratos mostra as colunas **API (30 dias)** e **Widgets (30 dias)**, e o botão **Ver uso** abre o detalhe **por dia** (dias em UTC-0) das requisições da API e das leituras de widgets. O limite é de 60 requisições por minuto por contrato. Dados em tempo real (MQTT) não contam no limite, e por isso são o caminho recomendado para quem quer dados "ao vivo".

![Uso diário de um contrato de API](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_contract_usage.png)

A **Central de Ajuda** ganhou uma página de **documentação da API**, com a descrição das rotas, o formato dos dados, exemplos de código e orientações de boas práticas, e os exemplos e as imagens ficam em um repositório público de exemplos.

![Página de documentação da API na Central de Ajuda](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_docs_page.png)

### Widgets para colar no seu site

Quer mostrar a temperatura da sua estufa na página da sua empresa, sem escrever uma linha de integração? A partir de um contrato, você cria um **widget**: escolhe o sinal (dentro do que o contrato permite), o tipo de gráfico e o visual, vê o resultado numa **pré-visualização** e copia o **Código de incorporação**, um `<script>` pronto para colar no site.

O widget **atualiza sozinho** em tempo real e aceita os tipos de gráfico mais usados: gráficos lineares, medidores, recipientes, indicadores, mapa de calor, histograma e outros.

![Widget do Seu IoT rodando em uma página HTML externa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/widget_embedded_external_page.gif)

**Por que é seguro colar:** a página pública **nunca recebe a chave do contrato**. Cada widget tem uma credencial **própria**, limitada exatamente aos sinais que ele mostra, e que você pode **revogar individualmente** sem afetar o resto. Revogou? A página que já tinha o código passa a mostrar "widget desativado pelo dono", sem você precisar mexer no site. Também dá para regenerar o código de incorporação, o que faz o `<script>` antigo parar de funcionar.

---

## Conecte uma IA ao Seu IoT (MCP)

O Seu IoT agora pode ser operado por **assistentes de IA** (Claude, Cursor, Gemini CLI e qualquer cliente compatível com o protocolo **MCP**). A IA vira mais uma interface sobre a sua conta: ela **enxerga só os projetos que você liberar** e **faz só o que você permitir**.

Você pede, em linguagem natural, coisas como "liste os dispositivos offline do projeto Estufa", "crie um gráfico de calendário da temperatura do último mês" ou "monte a leitura I2C deste sensor", e a IA faz o trabalho.

### Você decide o que a IA pode fazer

Ao conectar, o Seu IoT abre a tela **Autorizar acesso à sua conta**: você escolhe os **projetos** e, numa tabela de permissões, o que o app pode fazer. Cada permissão tem duas opções: **Permitir** e **Pedir minha confirmação**. No fim, **Autorizar** ou **Negar**.

| Permissão | A IA pode |
|---|---|
| Ver projetos | Listar projetos, dispositivos (online/offline), processos, triggers e gráficos |
| Ler dados | Consultar amostras e resumos (mínimo, máximo, média, p95, por hora/dia/semana/mês) |
| Editar projetos liberados | Criar e editar processos, triggers, gráficos e a posição dos cards |
| Criar novos projetos | Criar projetos novos |
| Apagar processos e ligações | **Pedir** para apagar processos, triggers e gráficos |
| Criar códigos de acesso | **Pedir** contratos de API, widgets incorporáveis e a primeira chave de acesso |
| Executar processos (play) | Executar um processo agora, como o botão de play |

![Tela Autorizar acesso à sua conta, com a tabela de permissões e a escolha dos projetos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_consent_screen.gif)

**O que a IA nunca faz:** apagar projetos ou dispositivos, apagar dados coletados, rotacionar chaves ou mexer em faturamento e administração. Isso fica sempre com você, na plataforma.

### Aprovações e transparência

- Quando uma ação exige confirmação, **nada é alterado** até você aprovar. A pendência aparece no sino de **Notificações**, com o **antes e depois** do que seria feito.
- **Chaves e tokens sempre exigem sua aprovação.** E você escolhe se a credencial vai **direto para a IA** (que a retira uma única vez, em até 15 minutos) ou se **só você a vê**.
- Em **Configuração > Apps conectados** você acompanha cada app, **amplia ou reduz** as permissões na hora e **revoga** com um clique.
- O botão **"O que este app fez"** mostra o histórico de tudo que o app leu e escreveu (inclusive o que foi recusado), sem nunca exibir credenciais.

![Fila de aprovações nas Notificações, com o antes e depois de uma alteração proposta pela IA](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_proposal_review.gif)

![Tela de Apps conectados com o histórico "O que este app fez"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_connected_apps.gif)

### Uma IA que não precisa adivinhar

A IA recebe **documentação dentro do próprio protocolo**: para cada tipo de processo (ADC, PWM, I2C, PID e os demais) e cada tipo de gráfico, ela consulta os **parâmetros válidos, o formato dos dados e exemplos prontos**, inclusive os pinos e canais corretos para a placa do projeto (ESP32 ou ESP32-S3). Ela também pode fazer um **ensaio** (validação sem criar nada) antes de propor uma mudança, e consultar **quais pinos estão livres**.

**Por que importa:** menos tentativa e erro, menos aprovações inúteis na sua fila, e resultados corretos já na primeira proposta.

> **Exemplo:** você pede "crie um processo que escreva no display I2C o valor lido pelo sensor". A IA consulta as fichas das operações, confere os pinos livres, valida o ensaio e só então envia **uma** proposta para você aprovar, com todos os parâmetros certos.

---

## Firmware 2.0.1

Duas mudanças no dispositivo (os processos e a plataforma funcionam com o firmware anterior, mas estes recursos dependem da atualização):

- **Editar um processo agora realmente atualiza o dispositivo.** Antes, ao alterar os parâmetros de um processo já criado, o dispositivo reexecutava o processo mas continuava usando a configuração antiga. Agora ele passa a usar os novos parâmetros imediatamente.
- **Escrita I2C acionada por trigger.** Quando uma **Escrita I2C** é acionada por outro processo (por exemplo, uma Leitura I2C ou um valor calculado), o dado recebido **vira o conteúdo enviado ao chip**. Números são convertidos em bytes na largura que você configurou (ex.: 65281 → `FF01`), e textos em hexadecimal são enviados como estão. O valor do trigger vale **só para aquela execução** e nunca sobrescreve o que está salvo no processo.

> **Exemplo:** um processo de PID calcula a potência e, via trigger, alimenta uma Escrita I2C que ajusta um conversor digital-analógico, tudo desenhado no Blueprint.

---

## Outras melhorias

- **Bit Banging Serial:** o pino de dados (DT) não era enviado corretamente ao dispositivo, que acabava lendo sempre no pino 0. Corrigido, e o card agora mostra os pinos **DT/SCK** no mesmo estilo dos pinos SDA/SCL do I2C.
- **Mais estabilidade no Blueprint:** ao voltar para a aba do navegador, a tela não sobrescreve mais uma alteração que você acabou de fazer em comentários, gráficos, processos e triggers.
- **Layout de calibração no celular:** as áreas de Linearização e Qualificação deixaram de "colapsar" em telas pequenas.
- **Notificações:** agora é possível abrir o **detalhe** de cada notificação numa janela.
- **Suporte:** novo fluxo para **abrir um ticket de suporte** direto pela plataforma.
- **Login:** depois de entrar, você volta para a página que tentava acessar.
- **Blog:** cada post agora exibe o **autor**, e o índice de tópicos aparece também nas versões para buscadores e redes sociais.

---

## Resumo das novidades

| Área | O que muda para você |
|---|---|
| Criação de gráficos | Tela própria com escolha do tipo e pré-visualização; painéis com sinais de vários projetos; modo Tela cheia |
| Novos gráficos | 14 tipos de indicador, medidor, recipiente, mapa de calor, histograma, linha/área por faixa e linhas de referência |
| Tabelas e mapas | Regra de dispositivos entre projetos; colunas de identidade, KPI, medidor, gráfico e ação; mapa com dados informativos |
| Conexão | Histórico online/offline, status em tempo real e quatro sinais de conectividade para gráficos |
| Armazenamento | Lixeira por projeto e uso somado de repositórios e projetos |
| Publicação automática | Ícone de envelope no processo e padrão por projeto |
| API aberta | Contratos de API com chave, MQTT em tempo real, controle de uso e documentação |
| Widgets | Código de incorporação para colar em qualquer site, com credencial própria e revogação |
| IA via MCP | Assistentes de IA com permissões, aprovações, auditoria e documentação embutida |
| Firmware 2.0.1 | Edição de processo aplicada no dispositivo e Escrita I2C acionada por trigger |

---

**Já está tudo no ar.** Crie um indicador, um medidor ou um mapa de calor, monte uma tabela com os dispositivos de vários projetos, abra um contrato de API e cole um widget no seu site, ou conecte a sua IA favorita e peça para ela montar algo para você. Atualize também o firmware dos seus dispositivos para a **2.0.1**. Conte para a gente o que achou: **seu feedback guia as próximas versões.**
