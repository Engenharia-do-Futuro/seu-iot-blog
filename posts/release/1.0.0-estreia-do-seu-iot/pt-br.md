![Capa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Seu IoT 1.0: a estreia da plataforma como ela sempre foi idealizada

**O Seu IoT foi evoluindo passo a passo, conforme a necessidade de cada projeto, mas a ideia original sempre foi chegar aqui. Remodelamos todo o sistema operacional da plataforma para sustentar essa visão.**

**Versão:** 1.0.0 | **Data:** 2026-08-16

---

Chegamos na versão **1.0.0**, e com ela a verdadeira estreia do Seu IoT como ele foi pensado desde o início. Ao longo do caminho, a plataforma foi evoluindo conforme a necessidade de cada cliente e de cada projeto, um recurso aqui, uma tela ali. Mas a ideia original sempre foi outra: colocar você para **desenhar o funcionamento do seu sistema**, não apenas cadastrar dispositivos e preencher formulários. Para chegar lá, remodelamos todo o **sistema operacional** do Seu IoT, e é esse trabalho que este texto apresenta.

O centro de tudo é a nova página de **Projetos**, um quadro visual estilo "planta técnica" onde você cria **processos**, liga um ao outro com **triggers** e vê a leitura de cada sensor em tempo real, direto no card. É a parte de que mais nos orgulhamos nesta versão: ficou muito mais dinâmico montar um projeto, mais livre para organizar do seu jeito, sem perder a praticidade do dia a dia.

![Visão geral do canvas Blueprint de um projeto, com processos conectados por triggers](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_overview.gif)

---

## Projetos: um novo jeito de organizar seus dispositivos

Os **Projetos** chegam para substituir e complementar os antigos Repositórios. Cada projeto tem **nome**, **descrição**, **tags livres** (com sugestão automática das tags que você já usou) e um **ícone** escolhido entre **78 opções** organizadas por tema.

**O que você ganha:**

- **Busca e filtros:** encontre projetos por nome, descrição ou tag, e filtre pela combinação de tags que quiser.
- **Ordenação:** por nome, data de criação/edição ou número de dispositivos.
- **Duas visualizações:** cards ou tabela no computador; no celular, sempre em cards.
- **Ajuda contextual:** uma explicação de "O que é um projeto?" tanto na tela vazia quanto por um botão de ajuda, para quem está começando.

![Página de Projetos com busca, filtro por tags e alternância entre cards e tabela](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/projects_page_overview.gif)

**Por que importa:** o menu lateral foi reorganizado e "Repositórios" virou uma seção legada, exibida apenas para quem ainda tem repositórios, que também passaram a ser listados logo abaixo dos projetos. Ninguém perde nada, mas o caminho recomendado a partir de agora é o Projeto.

Vincular e desvincular dispositivos também ficou mais claro: um modal separa **"Neste projeto"** de **"Outros dispositivos"** (com busca), e a contagem de dispositivos no card ou na tabela agora é **clicável**, abrindo esse modal direto.

![Modal de vínculo de dispositivos ao projeto, separando "Neste projeto" de "Outros dispositivos"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/project_device_link_modal.gif)

Outras novidades da página de projeto: o endereço agora usa um **nome amigável** baseado no título (em vez de um código longo), e existe uma nova **página de configurações** do projeto — microcontrolador, tipo de rede, contadores de processos por tipo, lixeira e links de provisionamento/calibração. Tudo traduzido em **português, inglês e espanhol**.

---

## O canvas Blueprint: o coração desta estreia

Aqui está a maior novidade da versão. A página do projeto virou um **quadro visual estilo "planta técnica"**, com efeito cianotipo, onde você **arrasta**, dá **zoom** e organiza os elementos do jeito que fizer mais sentido para o seu processo, sem grade fixa, sem hierarquia forçada.

![Canvas Blueprint com zoom e organização livre dos processos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_canvas_pan_zoom.gif)

**Por que importa:** montar um projeto deixou de ser preencher formulários em sequência e virou desenhar o funcionamento do seu sistema, o que deixa tanto a criação quanto a leitura do projeto muito mais intuitivas, principalmente quando há vários processos se relacionando.

### O que compõe o quadro

- **Cartão fixo de identificação:** um cartão no canto mostra ícone, nome, datas de criação/edição, número de dispositivos e dono do projeto, sempre visível, mesmo navegando pelo quadro.
- **Comentários:** crie, edite com formatação simples (**negrito**, *itálico*, ~~riscado~~), mova, redimensione e exclua comentários direto no quadro. O texto salva sozinho ao clicar fora, com opção de desfazer.

![Criação e edição de um comentário no Blueprint, com formatação e salvamento automático](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_comments.gif)

- **Gráficos como cards:** os gráficos também foram adaptados para os projetos, agora são mais um tipo de card, que você posiciona livremente no Blueprint. Escolha os processos, o período de tempo, o agrupamento de eixo e o tipo de gráfico (linha, barra, degrau, área, dispersão ou pizza), com pré-visualização ao vivo durante a configuração.
- **Minimapa colorido por categoria:** veja o projeto inteiro em miniatura, com cada processo colorido pela sua categoria e as linhas de ligação entre eles também representadas.
- **Busca no quadro:** procure por nome, filtre por tipo de item, e a visão **centraliza automaticamente** no resultado, útil em projetos com muitos processos.

![Minimapa colorido por categoria e busca dentro do canvas centralizando a visão](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_minimap_search.gif)

- **Carregamento com personalidade:** uma tela de loading animada evita a tela branca ao abrir um projeto.
- **Vincular Dispositivo:** um botão no cabeçalho do projeto mostra os dispositivos vinculados, com busca, status online/offline e localização aproximada.

![Botão "Vincular Dispositivo" no cabeçalho, mostrando dispositivos com status e localização](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_link_device.gif)

### E no celular?

O Blueprint ganhou uma versão adaptada para telas pequenas: barra superior simplificada, alternância entre informações do projeto e minimapa, e alças maiores para facilitar o toque.

![Versão do canvas Blueprint adaptada para celular](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_mobile.gif)

---

## Tipos de Processo: criar já explica como funciona

Cada tipo de processo agora tem uma **tela própria de criação**, com **diagramas animados** mostrando como aquele parâmetro se comporta, não é mais um formulário genérico de campos soltos. Essa é a outra parte de que mais gostamos nesta versão: dá para entender o que está configurando enquanto configura.

![Tela de criação de um processo com diagramas animados explicando o parâmetro](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_creation_animated_diagram.gif)

Processos disponíveis nesta versão:

- **ADC (leitura analógica):** pino, resolução, atenuação e número de amostras, com diagramas mostrando a conversão do sinal e o efeito de cada parâmetro na leitura.
- **Leitura Digital / Escrita Digital:** liga/desliga de pinos, com diagramas explicando ruído na leitura e a necessidade de amplificar o sinal (transistor/relé) na escrita.
- **Contagem de Pulsos:** conta pulsos elétricos, com opção de contar por borda de subida/descida e filtro de ruído.
- **PWM:** controle de intensidade (duty cycle) e frequência, com fade suave configurável.
- **Bit Banging Serial:** leitura de sensores com protocolo serial simples (dado + clock).
- **PID:** controle Proporcional-Integral-Derivativo, com **gráfico ao vivo** mostrando como cada ganho afeta a resposta do sistema controlado.

![Tela de configuração de PID com gráfico ao vivo mostrando o efeito dos ganhos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_pid_live_chart.gif)

- **Linearização:** converte a leitura bruta de outro processo numa unidade real (ex.: tensão → temperatura), calculando automaticamente a reta e a equação a partir de pontos de calibração informados por você.
- **Qualificação:** classifica a leitura de outro processo em faixas nomeadas por você (ex.: "baixo/médio/alto").

Três processos desta versão são novidade a ponto de merecerem uma seção própria, logo a seguir: **I2C**, **Máscara de Bits** e **Timer / Timeout**.

### Catálogo, execução e leitura em tempo real

Todos os tipos ficam organizados num **catálogo por categoria** (Periféricos, Eventos, Processamento de Dados), com busca e filtro. Tipos ainda não implementados aparecem com o selo **"em breve"**.

![Catálogo de tipos de processo organizado por categoria, com busca, filtro e selo "em breve"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_catalog.png)

- Cada processo tem **nome personalizável** (com sugestão automática "Processo N").
- Um botão **"Executar"** no card força uma nova execução sem precisar reconfigurar nada.
- O card do processo no canvas mostra a **leitura mais recente em tempo real**, e pode alternar para um **mini gráfico de histórico**, com cor e ícone conforme a categoria.

![Card de processo no canvas alternando entre leitura em tempo real e mini gráfico de histórico](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_realtime_card.gif)

- **Detecção automática de conflitos:** a plataforma identifica pinos/canais já ocupados por outros processos, evitando erro de configuração.
- **Confirmação visual:** o sistema agora mostra quando o dispositivo aplicou de fato o processo criado ou editado, em vez de deixar você sem retorno.

No celular, a tela de criação de processo fica **simplificada**, só a tabela de parâmetros, sem os diagramas animados.

---

## I2C: um protocolo de comunicação totalmente novo

O **I2C** é o processo mais original desta versão: um protocolo de comunicação novo no Seu IoT, criado do zero para conversar com sensores e periféricos que usam esse barramento, muito comum em sensores de temperatura, umidade, pressão, acelerômetros, displays e uma infinidade de outros módulos.

A implementação chega em quatro processos: **Canal** (define o barramento e os pinos de dados/clock), **Leitura**, **Escrita** e **Varredura**. Como os demais processos desta versão, a tela de configuração vem com diagramas explicando como o barramento funciona.

![Configuração do canal I2C com diagrama do barramento](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_i2c_channel.gif)

A **Varredura** funciona como um "scanner": ela percorre o barramento e mostra, numa grade de endereços, quais dispositivos I2C estão respondendo, útil tanto para conferir a fiação quanto para descobrir o endereço de um sensor novo antes de configurar a Leitura.

![Varredura I2C mostrando a grade de endereços dos dispositivos conectados ao barramento](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_i2c_scan.gif)

**Por que importa:** o I2C abre a porta para uma família muito maior de sensores compatíveis com o Seu IoT, inclusive os que combinam vários dados num único chip, o que passa a fazer sentido junto com a próxima novidade.

### Máscara de Bits: separando o que vem junto no mesmo dado

Muitos sensores I2C devolvem, num único valor lido, **mais de uma informação junta**, por exemplo, alguns bits do dado representam a leitura em si, e outros bits representam uma flag de status ou uma segunda grandeza. A **Máscara de Bits** foi criada especialmente para tratar esse cenário: um processo que **extrai uma parte específica** de um valor lido por outro processo, isolando só os bits que interessam.

![Configuração de uma Máscara de Bits extraindo parte de um valor lido via I2C](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_bitmask.gif)

**Por que importa:** sem esse processo, você precisaria tratar o dado bruto fora da plataforma para separar o que vem misturado num único valor. Com a Máscara de Bits, essa separação acontece dentro do próprio Blueprint.

> **Exemplo:** um sensor I2C devolve um valor de 16 bits em que os 12 bits mais baixos são a leitura de temperatura e os 4 bits mais altos são um código de status. Configure duas Máscaras de Bits sobre a mesma Leitura I2C, uma isolando os 12 bits da temperatura, outra isolando os 4 bits do status, e trate cada uma como um processo independente no seu projeto.

---

## Timer / Timeout: a amostragem virou um processo

Em Repositórios, a taxa de amostragem, de quanto em quanto tempo um sensor é lido, era configurada **dentro de cada processo**: ADC, Contagem de Pulsos, Leitura Digital e Bit Banging Serial, cada um com seu próprio campo de intervalo, isolado dos demais.

Agora existe um processo dedicado para isso: o **Timer / Timeout**. Você configura o intervalo uma vez (dias, horas, minutos ou segundos) e **conecta esse Timer, via trigger, a um ou mais processos** que devem ser acionados por ele. O card do Timer mostra uma **contagem regressiva visual** até o próximo disparo.

![Processo Timer configurado com contagem regressiva e ligado a outros processos por triggers](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_timer_triggers.gif)

**Por que importa:** o mesmo ritmo de amostragem passa a ser **reaproveitável** entre vários processos, em vez de repetido em cada um, e fica visível no Blueprint quem é acionado por qual Timer.

> **Exemplo:** um Timer de 30 segundos ligado a três processos diferentes, um ADC de temperatura, uma Leitura Digital de um sensor de porta e uma Varredura I2C. Os três são executados juntos, no mesmo ritmo, sem precisar repetir a configuração de tempo em cada um.

---

## ESP32-S3: a primeira variação de dispositivo suportada

Até aqui, todo projeto no Seu IoT partia de um único hardware de referência: o ESP32 original. Nesta versão chega a **primeira variação de dispositivo suportada** pela plataforma: o **ESP32-S3**.

Na página de configurações do projeto, você define **para qual modelo de dispositivo** aquele projeto é, ESP32 ou ESP32-S3. A partir dessa escolha, as telas de configuração de processo passam a respeitar os **limites de pinos corretos daquele modelo**, evitando que você configure um pino que não existe ou já tem função reservada na placa.

![Configuração do projeto definindo o modelo de dispositivo, ESP32 ou ESP32-S3](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/esp32_s3_project_config.png)

E não é só configuração: também já é possível **gravar o firmware em dispositivos ESP32-S3** pelo fluxo de instalação da plataforma, do mesmo jeito que já era feito com o ESP32.

![Gravação de firmware num dispositivo ESP32-S3 pelo fluxo de instalação](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/esp32_s3_flashing.gif)

**Por que importa:** é o primeiro passo de um caminho maior, oferecer suporte a diferentes variações de hardware dentro do mesmo projeto e do mesmo fluxo, sem que você precise aprender uma plataforma diferente para cada placa.

---

## Triggers: ligue processos com um traço

É possível **ligar processos entre si** desenhando uma linha da saída de um card até a entrada de outro, por exemplo, uma **contagem de pulsos** aciona um **PWM**.

![Ligação sendo desenhada entre dois processos no canvas, criando um trigger](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/triggers_connecting.gif)

- Uma **seta** indica o sentido do fluxo; a linha usa **gradiente de cor** entre as categorias de origem e destino.
- O sistema avisa quando você tenta **clicar** em vez de **arrastar** para criar a ligação.
- Ao excluir um processo, as ligações associadas a ele **desaparecem automaticamente**.

**Por que importa:** é a peça que transforma um conjunto de processos isolados numa automação de verdade, tudo desenhado, tudo visível, sem precisar abrir um formulário separado para configurar "se isso, então aquilo".

> **Exemplo:** ligue uma **Contagem de Pulsos** de um sensor de vazão a um **PWM** que controla uma bomba, para que a intensidade da bomba responda automaticamente ao fluxo medido, tudo visível como uma linha entre os dois cards no Blueprint.

---

## Navegação e usabilidade geral

Uma série de ajustes torna a plataforma mais fluida no dia a dia:

- Diversos botões e cards que antes só navegavam ao clicar viraram **links de verdade**, dá para abrir em nova aba com o botão direito ou Ctrl/Cmd+clique.
- **Menu lateral reorganizado** em grupos (Visão geral, Organização, Monitoramento, Dispositivos, Sistema), com ícones atualizados.

- Nova tela **"hub" de vínculo de dispositivo**, reunindo Instalar / Conectar / Links de Provisionamento num único lugar, com prévia animada de cada etapa.
- **Página inicial (Welcome) reformulada:** cards de projetos e dashboards recentes, guia rápido em passo a passo numerado, mini blog com últimos posts e card de armazenamento clicável.


- Novo **favicon** (ícone da aba do navegador).
- Botão **"Voltar ao site"** no cabeçalho da plataforma.
- Opção de vincular um dispositivo **"sem projeto nem repositório"** ao instalar ou editar o dispositivo.

---

## Outras novidades desta versão

Algumas melhorias que vieram junto, em áreas separadas do que apresentamos até aqui:


- **Isolamento de credenciais no MQTT:** cada dispositivo agora tem seu próprio login no broker MQTT, o canal por onde ele troca dados com a plataforma, restrito por uma **ACL** (lista de controle de acesso) apenas aos tópicos daquele dispositivo específico. Essa credencial continua sendo renovada automaticamente todos os dias, como já acontecia antes, mas agora é única por dispositivo. Na prática, isso isola o risco de uma violação física: se alguém extrair as credenciais de um dispositivo, elas só dão acesso aos dados daquele dispositivo, e os canais de comunicação de todos os outros permanecem protegidos.
- **SSL no HTTP e MQTT WebSocket:** comunicação passa a ser criptografada nesses canais, sem mudança visível na tela, mas mais segurança.
- **Canal de feedback:** novo formulário para você enviar feedback direto pela plataforma.

- **Blog com capa:** os cards de listagem do blog passam a mostrar a imagem de capa do post, com imagem padrão quando não há capa definida.

---

## Resumo das novidades

| Área | O que muda para você |
|---|---|
| Projetos | Novo conceito com nome, descrição, tags, ícone, busca, filtros e ordenação |
| Canvas Blueprint | Projeto vira um quadro visual: arraste, dê zoom, comente, use minimapa, busca e gráficos como cards |
| Tipos de Processo | Telas próprias com diagramas animados e catálogo por categoria |
| I2C e Máscara de Bits | Novo protocolo de comunicação, com Canal, Leitura, Escrita e Varredura; extraia partes de um valor lido |
| Timer / Timeout | Amostragem virou um processo dedicado, que aciona outros processos por trigger |
| ESP32-S3 | Primeira variação de dispositivo suportada, com limites de pinos e gravação próprios |
| Triggers | Conecte processos desenhando uma linha, com seta e gradiente de cor |
| Segurança | Credenciais MQTT exclusivas por dispositivo (ACL) e SSL em HTTP e MQTT WebSocket |
| Feedback | Formulário de feedback direto na plataforma |

---

**Já está tudo no ar.** Abra um projeto e veja o Blueprint pela primeira vez, crie um processo, observe as animações explicando cada parâmetro e ligue dois processos com um trigger. É a versão que sempre quisemos entregar, e agora ela finalmente existe. Conte para a gente o que achou: **seu feedback guia as próximas versões.**
