![Capa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Novidades: Configuração por Bluetooth, Personnas e Links de Provisionamento

**Data:** Maio de 2026 | **Versão:** v0.16.2

---

Essa atualização traz mudanças grandes na forma como você configura e distribui dispositivos. Se você usa o Seu IoT para gerenciar sensores em campo, instalar dispositivos para clientes, ou escalar sua operação — essa versão foi feita para você.

---

## Configuração via Bluetooth direto do navegador

Antes, para conectar um novo dispositivo à plataforma, era necessário entrar no modo AP: conectar no Wi-Fi do próprio dispositivo, abrir uma página de configuração, digitar os dados da rede — um processo mais chato, especialmente em campo.

**Agora você configura qualquer dispositivo por Bluetooth, direto do seu navegador**, sem precisar trocar de rede Wi-Fi ou instalar aplicativo nenhum.

### Como funciona na prática

1. Abra a página de configuração do dispositivo no Seu IoT
2. Clique em **Conectar via Bluetooth**
3. Selecione o dispositivo na lista que aparece no navegador
4. O sistema detecta automaticamente o firmware, o endereço MAC e o status atual
5. Você escolhe a rede Wi-Fi, o repositório ao qual o dispositivo vai pertencer, e pronto

![Configuração via Bluetooth](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/ble-provisioning.png)

A conexão é **criptografada** — o firmware do dispositivo e o servidor trocam chaves de segurança antes de qualquer configuração ser enviada, então os dados da sua rede Wi-Fi viajam de forma protegida.

> Exemplo: você chegou a um cliente com 5 novos dispositivos. Em vez de conectar no AP de cada um separadamente, você faz tudo de uma vez pela tela do notebook, por Bluetooth, sem sair da plataforma.

---

## Personnas: associe dispositivos a clientes e operadores

Surgiu uma necessidade prática para quem gerencia dispositivos de múltiplos clientes: **quem é o responsável por aquele dispositivo? Qual cliente está associado a ele?**

A nova seção de **Personnas** resolve isso. Uma Personna é um cadastro de pessoa ou empresa que você vincula aos seus dispositivos.

### O que você pode registrar em uma Personna

- Nome completo ou razão social
- CPF, CNPJ ou Tax ID (para clientes internacionais)
- Endereço completo (rua, número, bairro, cidade, estado, CEP)
- Contatos: e-mail, telefone ou WhatsApp
- Papel: **cliente** (quem usa o dispositivo) ou **operador** (quem mantém)

### Para que serve

- Você instala um sensor de temperatura na fábrica de um cliente → cadastra o cliente como Personna e vincula ao dispositivo
- Se precisar ligar para avisar de uma manutenção, os contatos já estão ali
- Você vê, direto na tabela de dispositivos, qual cliente está associado

---

## Links de Provisionamento: deixe seu cliente configurar o próprio dispositivo

Essa é uma das funcionalidades mais poderosas desta versão. Você pode **gerar um link ou QR Code** e enviar para o seu cliente. Quando ele abre o link, um fluxo guiado aparece para que ele mesmo conecte o dispositivo à plataforma — **sem precisar ter conta no Seu IoT**.

### Por que isso importa

Pense em uma distribuidora que vende 200 sensores por mês. Antes, alguém da equipe técnica precisaria configurar cada um. Agora, o próprio cliente recebe um link, abre no celular ou notebook, e conclui a configuração por Bluetooth em minutos.

### Controles que você tem ao criar o link

- **Nome do link** — para você identificar de qual campanha ou cliente é
- **Repositório de destino** — para qual projeto os dispositivos vão entrar
- **Limite de usos** — quantos dispositivos podem ser configurados pelo link
- **Validade** — o link pode expirar em uma data específica
- **Associação automática a uma Personna** — o cliente preenche os dados dele durante o fluxo, e já fica cadastrado

![Links de Provisionamento](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/provisioning-links.png)

O link gera automaticamente um **QR Code** que você pode imprimir, colocar no box do produto, ou enviar por e-mail.

> Exemplo: você fecha um contrato com 50 unidades. Cria um link de provisionamento com limite de 50 usos e validade de 30 dias. Envia o link para o seu cliente. Ele configura os dispositivos no próprio ritmo, e tudo cai no repositório correto na sua conta.

![Provisionamento via Link](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/ble-provisioning-from-provisioning-link.png)

---

## Mapa de localização dos dispositivos

Durante a configuração por Bluetooth, o navegador agora **captura a localização geográfica** (com permissão do usuário) e salva as coordenadas do dispositivo.

Na página de dispositivos, você pode **alternar para a visão de mapa** e ver onde cada dispositivo está instalado. Dispositivos próximos se agrupam automaticamente no mapa para facilitar a visualização.

![Mapa de dispositivos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/device-list-in-map.png)

> Útil para quem tem dispositivos espalhados em várias cidades ou regiões — é possível ver de relance se alguma área está com mais dispositivos offline, por exemplo.

---

## Gravação de firmware mais confiável

Uma correção importante: antes de gravar o firmware no dispositivo, a memória flash é **completamente limpa primeiro**. Isso resolve casos onde o dispositivo ficava em estado inconsistente após uma atualização, especialmente quando a gravação anterior havia sido interrompida.

---

## Documentação completa da plataforma

A plataforma agora tem uma **documentação oficial** disponível em português e inglês, acessível pelo menu Ajuda. Ela cobre desde como conectar o primeiro dispositivo até como usar dashboards, calibrar sensores e entender as regras de armazenamento de dados.

---

## Resumo das novidades

| Funcionalidade | O que muda para você |
|---|---|
| Configuração via Bluetooth | Configura dispositivos pelo navegador, sem AP mode |
| Comunicação criptografada | Seus dados de rede Wi-Fi são transmitidos com segurança |
| Personnas | Associe clientes e operadores a cada dispositivo |
| Links de Provisionamento | Envie um link/QR Code para clientes configurarem sozinhos |
| Mapa de dispositivos | Veja onde seus dispositivos estão instalados |
| Flash limpa antes de gravar | Gravação de firmware mais confiável |
| Documentação | Guia completo da plataforma em PT e EN |
