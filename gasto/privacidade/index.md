---
title: Política de Privacidade Geral do Gastô
lang: pt-BR
---

# Política de Privacidade Geral

- **Vigência:** a partir do lançamento do Gastô
- **Controlador de dados pessoais:** DIEGO SOGARI
- **Contato de privacidade:** privacy@sogari.cc

## Importação de notas fiscais

O Gastô permite importar uma nota fiscal eletrônica de consumidor (NFC-e) pelo link de consulta. A consulta começa assim que a câmera lê o código QR ou quando você toca em **Importar via link** após informar o endereço manualmente.

O Gastô usa a câmera apenas para ler o código QR. Durante a leitura, o aplicativo não grava nem envia imagens da câmera.

Para buscar a nota, o Gastô faz uma consulta por HTTPS ao endereço indicado no link. O aplicativo limita a consulta e eventuais redirecionamentos a endereços sob o domínio `gov.br`. O servidor que recebe a consulta tem acesso aos parâmetros do link e pode receber dados da conexão, como o endereço IP.

O Gastô processa a resposta no dispositivo, extraindo os dados do estabelecimento, itens comprados e seus detalhes, totais, formas e valores de pagamento e metadados fiscais da nota. O Gastô também inclui a versão do aplicativo nos dados da importação.

O Gastô identifica o município do emitente pelo endereço informado na nota. Quando consegue resolver o município, o aplicativo guarda o código IBGE do município, seu fuso horário e a data e hora de emissão. A consulta à tabela de municípios e fusos horários ocorre no dispositivo.

O Gastô não pede nome, e-mail, CPF ou outros identificadores do comprador nem os extrai da página consultada como campos separados. Entretanto, o link de consulta poderá conter CPF ou outro identificador do destinatário, especialmente em notas emitidas em contingência. [Nota Técnica 2025.001 da NFC-e (PDF)][nota-tecnica-nfce]

O Gastô usa esses parâmetros na consulta e os preserva no link do código QR gerado para compartilhamento. Quem receber esse código poderá usá-lo para consultar a nota.

Na versão atual, o Gastô não envia os dados extraídos da nota nem a página consultada a servidores do desenvolvedor.

## Armazenamento

O histórico de notas fica em memória enquanto o aplicativo está em execução. O Gastô não salva esse histórico no dispositivo nem em servidores e não faz backup automático dos dados. As preferências de ajuste do aplicativo são guardadas no próprio dispositivo.

## Importação e exportação de arquivos JSON

Ao selecionar **Importar JSON**, você pode escolher um ou mais arquivos. O Gastô lê no dispositivo os dados das notas e os metadados de importação salvos nesses arquivos. Essa opção não consulta o portal fiscal nem solicita a localização do dispositivo.

O arquivo exportado preserva os parâmetros do link de consulta, que podem incluir CPF ou outro identificador do destinatário. Quem receber o arquivo poderá usar o link para consultar a nota. Quando disponíveis, o código IBGE do município do emitente e a data e hora de emissão também são incluídos no arquivo.

Você pode exportar uma nota individualmente ou usar **Exportar seleção** no histórico para gerar um arquivo JSON separado para cada nota selecionada.

Ao exportar, poderá guardar os arquivos localmente ou escolher o seu iCloud Drive para manter cópias privadas. Caso escolha outro destino ou compartilhe os arquivos, as cópias estarão sujeitas às regras do serviço ou do destinatário escolhido. Você pode apagar os arquivos exportados via sistema de arquivos ou pelo serviço em que os salvou.

## Seus direitos e como entrar em contato

Use o contato de privacidade informado no início desta política para tirar dúvidas ou exercer seus direitos em relação aos dados pessoais tratados pelo controlador. Conforme a LGPD, você pode pedir confirmação de tratamento, acesso, correção, informação sobre compartilhamento e, quando aplicável, bloqueio, anonimização, portabilidade ou exclusão.

Você também pode revogar seu consentimento e apresentar uma petição à Autoridade Nacional de Proteção de Dados (ANPD). [Direitos dos titulares na ANPD][direitos-titulares-anpd]

Caso entre em contato, usaremos os dados que você fornecer para responder e atender ao pedido. Manteremos a correspondência de privacidade enquanto o pedido estiver em andamento e por até 30 dias após seu encerramento. Se uma obrigação legal ou uma controvérsia em andamento exigir retenção por mais tempo, conservaremos apenas as informações necessárias pelo prazo aplicável.

Para documentar o atendimento de pedidos formais, poderemos manter um registro separado com o número do caso, as datas de recebimento e encerramento, o tipo de pedido e a providência tomada. Se for necessário incluir algum dado pessoal nesse registro, ele será mantido apenas enquanto for necessário para comprovar o atendimento ou cumprir uma obrigação legal.

## Estatísticas de uso do aplicativo

A opção **Estatísticas de uso** vem desativada. Você pode ativá-la ou desativá-la em **Ajustes → Privacidade** a qualquer momento. Ao desativá-la, o Gastô descarta os resumos que ainda estão em memória e interrompe as medições.

Quando a opção está ativada, o Gastô calcula a contagem de amostras, a soma, o mínimo e o máximo de cada métrica abaixo. Também conta quantas amostras caem em cada uma de 16 faixas predefinidas. A média é calculada a partir da soma e da contagem.

- Duração das requisições ao portal fiscal, incluindo as que falham.
- Duração da análise do HTML recebido do portal.
- Duração do processamento das buscas no histórico de notas.
- Duração do processamento das buscas no catálogo de produtos.
- Tamanho em bytes do HTML recebido nas importações concluídas pelo portal.

As três métricas de importação pelo portal são agrupadas pela UF do emitente, extraída da chave de acesso da nota no dispositivo. Esses grupos permitem acompanhar o desempenho das importações e sua distribuição por UF.

As duas métricas de busca são registradas somente quando o resultado ainda não está em cache, sem contar a espera enquanto você digita, e são agrupadas por faixa de quantidade de notas no histórico ou de produtos no catálogo.

Os resumos ficam em memória. Quando o aplicativo passa para segundo plano, o Gastô tenta enviar os resumos, a versão do aplicativo e a versão do iOS por HTTPS a um serviço hospedado na Cloudflare. O Workers Analytics Engine registra o horário de recebimento e armazena os resumos por três meses. O desenvolvedor usa esses dados para acompanhar o desempenho do Gastô.

Enquanto **Estatísticas de uso** estiver ativada, a opção **Relatórios enviados** em Ajustes permite consultar a data, a hora e o JSON de cada envio bem-sucedido da sessão atual. Essa lista fica apenas em memória e é descartada quando o aplicativo é encerrado.

O Gastô não inclui no envio links, chaves de acesso, termos de busca, itens ou valores das notas, localização do dispositivo ou identificadores da conta ou do dispositivo. A Cloudflare recebe o endereço IP da conexão. O serviço usa esse endereço para limitar o volume de requisições e não o grava no conjunto de dados de estatísticas.

## Funcionalidades futuras e opcionais

Os recursos abaixo ainda não estão disponíveis. A presente política está atrelada à versão do aplicativo instalada em seu dispositivo. Ao oferecer um novo recurso, o Gastô apresentará a finalidade, os dados envolvidos, quem poderá acessá-los e como desativar a participação.

### Backup integrado

Se o Gastô oferecer backup integrado, o recurso será ativado somente com sua autorização. As cópias serão armazenadas na base de dados privada do Gastô no CloudKit, vinculada à sua conta do iCloud. A autorização para o backup se limita a essa finalidade. Você poderá desativar a opção a qualquer momento nos ajustes do aplicativo.

## Atualizações desta política

Atualizaremos esta política quando houver mudança na forma como o Gastô trata seus dados. Se uma nova finalidade depender de consentimento, pediremos sua autorização antes de iniciar o tratamento.

[nota-tecnica-nfce]: https://www.nfe.fazenda.gov.br/Portal/exibirArquivo.aspx?conteudo=NvuzQGYd6E8%3D
[direitos-titulares-anpd]: https://www.gov.br/anpd/pt-br/assuntos/titular-de-dados-1/direito-dos-titulares
