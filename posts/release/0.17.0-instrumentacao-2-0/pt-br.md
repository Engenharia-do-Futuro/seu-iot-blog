![Capa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Instrumentação 2.0: calibre sensores vendo o resultado em tempo real

**Calibração mais rápida e menos sujeita a erro, links de calibração (manuais e automáticos), nova página de Links e a plataforma agora em Espanhol.**

**Versão:** 0.17.0 | **Data:** 2026-06-19

---

Esta atualização traz o maior avanço na configuração de sensores desde o lançamento da plataforma: a **Instrumentação 2.0**. Se você calibra ou lineariza sensores, a nova tela mostra o resultado da sua configuração enquanto você digita — sem adivinhação. E tem mais: links de calibração para usar em campo (inclusive automáticos ao provisionar), uma nova página de Links, o Blog renovado e suporte completo a Espanhol.

![Visão geral da nova tela de Instrumentação 2.0](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/instrumentation_overview.png)

---

## Instrumentação 2.0: configure vendo o resultado

Reformulamos por completo a tela de instrumentação. O novo formulário organiza tudo em **dois métodos**, cada um na sua aba: **Qualificação** (classificar leituras em estados) e **Linearização** (ajustar a leitura bruta ao valor real). Tudo com **entrada numérica localizada** (o campo respeita o separador decimal do seu idioma) e gráficos que mostram, em tempo real, como o sensor vai responder.

---

### Qualificação: transforme leituras em classificações

O recurso antes chamado de *Quantização* agora se chama **Qualificação** — e ficou mais claro de usar.

**O que mudou:** a Qualificação permite **classificar as leituras** por **faixas de limiar**. Você cria uma lista de faixas, e cada faixa tem um **nome** e um **valor de limiar**. A regra é simples e única: *se a leitura for **maior ou igual** (`≥`) ao limiar, ela recebe o nome daquela faixa*.

Como funciona na prática:

- As faixas são **ordenadas automaticamente** (do maior limiar para o menor) e avaliadas de cima para baixo.
- A leitura recebe o nome da **primeira faixa** cujo limiar ela atinge.
- Existe uma faixa **"Padrão"** (capturar tudo), que classifica qualquer leitura que não atinja nenhum limiar.
- Uma **timeline lateral** mostra as faixas visualmente enquanto você as configura.

"Qualificar" uma leitura é, em poucas palavras, **dar um significado ao número bruto**. Em vez de mostrar apenas `82`, você define faixas que traduzem esse valor em um estado legível.

**Por que importa:** leituras viram estados/classificações úteis para dashboards e regras, de forma muito mais clara do que olhar números soltos.

> **Exemplo:** crie a faixa **"Crítico"** com limiar `80`, a faixa **"Alerta"** com limiar `60` e deixe a faixa **"Padrão"** como "Normal". Assim, uma leitura de `82` vira **"Crítico"**, `65` vira **"Alerta"** e `40` vira **"Normal"**.

> **Outro exemplo — temperatura:** imagine classificar a leitura de um termistor em estados de calor. Você cria as faixas **"Muito quente"** (`≥ 4000`), **"Quente"** (`≥ 3000`), **"Morno"** (`≥ 2000`) e **"Frio"** (`≥ 1000`), e deixa a faixa **"Padrão"** como **"Muito frio"** (capturar tudo abaixo disso). Assim, uma leitura de `3128` é classificada como **"Quente"**, `2400` como **"Morno"** e `500` como **"Muito frio"**. A timeline lateral mostra essas faixas empilhadas, do mais quente ao mais frio, conforme você as configura.

![Aba de Qualificação com faixas, limiares e timeline lateral](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/qualification_calibration.gif)

---

### Linearização assistida pelo dispositivo

A **Linearização** é o método da plataforma para converter a leitura bruta do sensor no valor real, ajustando uma reta a pontos de referência. Agora você define esses pontos com **dados reais do sensor**, capturados na hora.

**O que mudou:** ao linearizar, um **mini-gráfico "Leituras do dispositivo"** mostra os valores do dispositivo selecionado. Você ainda ganha:

- **Botão "Solicitar leitura"**: peça ao dispositivo que capture um dado **ao vivo**, na hora, sem esperar um envio agendado.
- **Seleção de pontos no gráfico**: selecione **um ou mais pontos** (arrastando para marcar um intervalo). Ao escolher vários, o sistema calcula a **média** deles e **preenche automaticamente** o valor do comparador no ponto de linearização.

**Por que importa:** linearizar fica mais rápido e preciso — você usa leituras reais do sensor, e a média **reduz o efeito de ruído** de medições individuais.

**Como usar:**

1. Selecione o **dispositivo** na tela de instrumentação.
2. Clique em **"Solicitar leitura"** para capturar um dado ao vivo.
3. **Arraste** sobre os pontos desejados no mini-gráfico.
4. O **valor comparativo é preenchido sozinho** (média dos pontos selecionados).

![Seleção de vários pontos no mini-gráfico preenchendo o valor do comparador](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/linearization_selection_of_points.gif)

---

### Feedback de linearização: saiba se o ajuste ficou bom

Ao adicionar os pontos de linearização, a plataforma **ajusta uma reta** e exibe um painel com **métricas de qualidade do ajuste**. Cada campo significa:

- **Intervalo calibrado** — a faixa de valores coberta pelos seus pontos de linearização. Leituras fora dela exigem extrapolação e podem ter precisão reduzida.
- **Equação (`y = ax + b`)** — a reta ajustada por mínimos quadrados; `a` é o ganho e `b` é o offset aplicados à leitura.
- **R²** — o coeficiente de determinação, de 0 a 1: quanto mais perto de 1, melhor o ajuste. Valores abaixo de ~0,99 podem indicar não-linearidade ou ruído.
- **σ (desvio padrão)** — a dispersão média entre os pontos e a reta ajustada; quanto menor, melhor.
- **Margem de erro (±2σ)** — o erro máximo esperado nas leituras calibradas, equivalente ao dobro do desvio padrão.

**Por que importa:** você sabe **na hora** se a linearização ficou boa, com uma estimativa **objetiva** do erro — em vez de "achar" que ficou certo.

![Curva de linearização com painel de feedback: Equação, R², σ e Margem de erro](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/linearization_calibration_curve.gif)

---

### Linearização diferente por dispositivo

A mesma instrumentação base agora pode ter **linearizações distintas por dispositivo** (variantes).

**Por que importa:** sensores do mesmo tipo costumam ter características únicas e respondem de forma diferente ao **mesmo ambiente**. Linearizar individualmente garante leituras corretas e **comparáveis** entre dispositivos.

> **Exemplo:** dois sensores de umidade idênticos, instalados lado a lado, marcam valores diferentes no mesmo local. Com uma linearização própria para cada um, ambos passam a reportar o valor correto.

![Linearizações distintas por dispositivo na mesma instrumentação](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/differents_calibrations_per_device.png)

---

## Calibração em campo: o link de provisionamento

Nem sempre quem calibra o sensor é quem está na plataforma. Por isso criamos um fluxo de **calibração via "magic link"**: você gera um link e o trabalho é feito por uma **página pública dedicada**, sem percorrer todo o fluxo da plataforma.

Importante: essa página pública **abre as mesmas ferramentas de instrumentação** — **Linearização** e **Qualificação**. Ou seja, a pessoa em campo executa a operação de verdade (tipicamente a **Linearização**, ajustando os pontos com leituras reais do sensor) e o resultado vira uma **variante daquele dispositivo**.

Um **modal** na tela do dispositivo permite gerar o link e acompanhar as sessões em andamento.

**Por que importa:** facilita a linearização em campo e permite **delegar a tarefa** a quem está fisicamente com o dispositivo — um técnico, um parceiro ou o próprio cliente.

**Como usar:**

1. Na tela do dispositivo, abra o **modal de geração do link de calibração**.
2. Compartilhe o link com quem fará a linearização.
3. Acompanhe as **sessões de calibração** pelo mesmo modal.

![Criação do link de calibração e calibração pela página pública via link](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/creating_calibration_link_and_calibration_by_link.png)

---

## Nova página de Links, com texto e imagens

Adicionamos uma **página de Links** à plataforma. Agora você pode configurar os **links automáticos de calibração** de um repositório.

**Por que importa:** compartilhar recursos, instruções e materiais com sua equipe ou seus clientes ficou mais claro e apresentável.

![Nova página de Links do repositório com texto e imagens](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/pagina_de_links_do_repositorio.png)

---

## Links de calibração automáticos ao provisionar

E se cada novo dispositivo já nascesse com os links de calibração prontos? Agora nasce. Você configura **uma única vez por repositório** e, a cada novo dispositivo provisionado via link de provisionamento, a plataforma **cria sozinha as sessões de calibração** das instrumentações que você escolheu.

**Para que serve:** quando você provisiona muitos dispositivos — principalmente em campo —, gerar um link manual para cada um é repetitivo. Com os links automáticos, quem está instalando já recebe tudo pronto e **calibra na hora**, sem ninguém precisar abrir a plataforma.

**Como funciona:**

- Você define quais **instrumentações** ganham calibração automática e a **duração padrão** dos links.
- A cada novo dispositivo provisionado pelo link de provisionamento, a plataforma cria **uma sessão de calibração por instrumentação selecionada** e gera os links correspondentes (cada um com sua validade).
- Nada precisa ser gerado manualmente para cada dispositivo.

**Como configurar:**

1. Acesse a página de **Links**.
2. Clique em **"Links automáticos"**.
3. No modal **"Links automáticos ao provisionar"**, selecione as **instrumentações** que devem receber calibração automática.
4. Defina a **duração padrão dos links**, em horas (mínimo 1; o padrão é **2 horas**).
5. **Salve a configuração**.

A partir daí, todo dispositivo novo provisionado pelo link de provisionamento já nasce com os links de calibração prontos.

![Edição do link de calibração automático ao provisionar](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/editing_automatic_calibration_link.gif)

---

## A plataforma agora fala Espanhol

O SEU IoT agora tem **suporte completo ao Espanhol (es-ES)**, incluindo **documentação** e **Termos de Uso**. Um novo **seletor de idioma com bandeiras** deixa a troca a um clique.

**Por que importa:** abrimos a plataforma para usuários de língua espanhola — mais alcance para você e para o seu produto.

![Troca de idioma para Espanhol pelo seletor com bandeiras](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/changing_language_to_spanish.gif)

---

## Blog renovado

O Blog ganhou uma boa repaginada:

- **Multi-idioma:** cada post pode ter versões em **Português, Inglês e Espanhol**, e você lê na língua selecionada na plataforma.
- **Conteúdo dinâmico:** os posts são publicados a partir de um repositório de conteúdo, então **novas publicações entram no ar sem precisar de um novo deploy** da plataforma.
- **Compartilhar com um clique:** copie o link do post ou compartilhe direto no **LinkedIn**.
- **Busca e filtros** por categoria, tags e data para achar o que interessa rapidinho.

![Post do blog com tags, botão de compartilhar e botão de retorno](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/blog_post_with_tags_share_and_return_button.png)

---

## SEO e compartilhamento: seus links bem apresentados

Nos bastidores, melhoramos como os links da plataforma e do blog aparecem por aí:

- **Pré-visualização bonita ao compartilhar:** ao colar o link de um post em redes sociais ou apps de mensagem, ele aparece com **título, descrição e imagem corretos** — as tags Open Graph passaram a ser geradas **no servidor**, inclusive para os crawlers dos buscadores.
- **Versões por idioma para o Google:** cada post sinaliza suas versões PT/EN/ES via **hreflang**, então a pessoa encontra o conteúdo no idioma dela.
- **Sitemap dinâmico:** o `sitemap.xml` agora é gerado automaticamente e **inclui os posts do blog**, ajudando a indexação.

**Por que importa:** mais gente encontra e compartilha o conteúdo — e ele aparece do jeito certo.

---

## Resumo das novidades

| Funcionalidade | O que muda para você |
|---|---|
| Instrumentação 2.0 | Linearize com dados reais do sensor, veja a qualidade do ajuste (R², σ, erro) e qualifique leituras em estados |
| Linearização por dispositivo | Linearização própria para cada dispositivo, mesmo na mesma instrumentação base |
| Calibração por link | Gere um link e delegue a linearização/calibração em campo |
| Links automáticos ao provisionar | Novos dispositivos já nascem com os links de calibração prontos |
| Página de Links | Compartilhe conteúdo com texto e imagens |
| Plataforma em Espanhol | Idioma es-ES completo, com docs e Termos de Uso |
| Blog renovado | Posts em PT/EN/ES, conteúdo dinâmico e compartilhamento |
| SEO e compartilhamento | Pré-visualização correta dos links, hreflang e sitemap dinâmico |

---

**Já está tudo no ar.** Entre na plataforma e abra a nova tela de instrumentação para sentir a diferença ao calibrar seu próximo sensor. Depois, conte para a gente: o que ficou melhor e o que você ainda gostaria de ver? **Seu feedback guia as próximas versões.**


